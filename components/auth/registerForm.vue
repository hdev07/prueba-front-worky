<template>
  <div class="p-6">
    <div class="mb-4">
      <p class="mb-1 text-center font-bold text-2xl">Register</p>
    </div>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-text-field
        v-model="name"
        type="name"
        name="nombre"
        :rules="nameRules"
        label="Full Name"
        outlined
        required
      />
      <v-text-field
        v-model="email"
        type="email"
        name="email"
        :rules="emailRules"
        label="E-mail"
        outlined
        required
      />
      <v-text-field
        v-model="password"
        type="password"
        name="password"
        :rules="passwordRules"
        label="Password"
        outlined
        required
      />
      <v-text-field
        v-model="passwordConfirmation"
        type="password"
        name="password"
        :rules="passwordRulesConfirmation"
        label="Confirm Password"
        outlined
        required
      />
      <div class="flex flex-wrap justify-between mt-5">
        <v-btn outlined color="black" class="mr-4" to="/login">Cancel</v-btn>
        <v-btn :disabled="!valid" color="primary" @click="validate">Register</v-btn>
      </div>
    </v-form>
    <Alert :alertType="alertType" :textAlert="textAlert" :snackbar="showAlert" />
  </div>
</template>

<script>
import Alert from "../common/alert.vue";
export default {
  components: { Alert },
  data() {
    return {
      valid: true,
      showAlert: false,
      alertType: "error",
      textAlert: "Invalid information",
      name: "",
      nameRules: [v => !!v || "Name is required"],
      email: "",
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+\..+/.test(v) || "E-mail must be valid"
      ],
      password: "",
      passwordRules: [v => !!v || "Password is required"],
      passwordConfirmation: "",
      passwordRulesConfirmation: [
        v => !!v || "type confirm password",
        v => v === this.password || "The password confirmation does not match."
      ]
    };
  },

  methods: {
    validate() {
      this.$refs.form.validate();
      if (this.$refs.form.validate() === true) {
        this.alertType = "success";
        this.textAlert = "User created successfully";
        this.showAlert = true;
        setTimeout(() => {
          this.showAlert = false;
          this.$router.push("/login");
        }, 1200);
      } else {
        this.showAlert = true;
        setTimeout(() => {
          this.showAlert = false;
        }, 2000);
      }
    }
  }
};
</script>