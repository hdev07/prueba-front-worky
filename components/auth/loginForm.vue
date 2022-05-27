<template>
  <div class="h-full w-full">
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-text-field
        color="primary"
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        outlined
        required
      />
      <v-text-field
        color="primary"
        v-model="password"
        type="password"
        :rules="passwordRules"
        label="Password"
        outlined
        required
      />
      <div class="flex flex-wrap justify-end mt-1">
        <nuxt-link to="/forgot-password">Forgot password</nuxt-link>
      </div>
      <div class="flex justify-between pt-5">
        <v-btn outlined color="black" class="mr-4" @click="goToRegister()">Register</v-btn>
        <v-btn :disabled="!valid" color="primary" @click="validate()">Validate</v-btn>
      </div>
    </v-form>
    <div v-show="showAlert">
      <Alert :alertType="'error'" :textAlert="'Password/Email not match'" :snackbar="showAlert" />
    </div>
  </div>
</template>
<script>
import Alert from "../common/alert.vue";
export default {
  components: { Alert },

  data: () => ({
    valid: false,
    showAlert: false,
    email: "alejandro@zentric.mx",
    emailRules: [
      v => !!v || "E-mail is required",
      v => /.+@.+\..+/.test(v) || "E-mail must be valid"
    ],
    password: "alejandro",
    passwordRules: [v => !!v || "Password is required"]
  }),
  methods: {
    validate() {
      this.$refs.form.validate();
      if (this.$refs.form.validate() === true) {
        this.email === "alejandro@zentric.mx" && this.password === "alejandro"
          ? this.$router.push("/dashboard")
          : console.error("error");
        this.valid = true;
      } else {
        this.showAlert = true;
        setTimeout(() => {
          this.showAlert = false;
        }, 2000);
      }
    },
    goToRegister() {
      this.$router.push("/register");
    }
  }
};
</script>
