<template>
  <div id="login-page" class="h-screen w-screen bg-img">
    <div class="h-full">
      <div class="w-full h-full flex items-center justify-center md:hidden">
        <div class="w-4/5 mx-auto rounded-lg">
          <img src="@/assets/images/logo.png" alt="LAE" class="p-4 size-image mx-auto" />
          <div class="flex w-5/6 mx-auto">
            <Login :redirect="redirect" />
          </div>
        </div>
      </div>
      <div
        class="w-2/5 lg:w-1/3 h-full flex-col justify-center items-center bg-white hidden md:flex padding-top"
      >
        <img src="@/assets/images/logo.png" alt="LAE" class="p-4 size-image" />
        <div class="flex w-5/6 mx-auto">
          <Login :redirect="redirect" />
        </div>
      </div>
      <div class="w-3/5 lg:w-2/3 bg-img hidden md:flex" />
    </div>
  </div>
</template>

<script>
import Login from "~/components/auth/loginForm";

export default {
  auth: false,
  layout: "empty",
  components: { Login },

  data: () => ({
    redirect: undefined
  }),
  methods: {}
};
</script>

<style scoped>
.size-image {
  max-width: 14rem !important;
}
.padding-top{
  padding-top: 20%;
}
</style>
