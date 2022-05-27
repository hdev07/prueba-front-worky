<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" :mini-variant.sync="mini" permanent clipped app>
      <v-list-item class="px-2">
        <img src="@/assets/images/logo.png" alt="LAE" class="w-14 p-2" />

        <v-list-item-title>Alejandro Cruz</v-list-item-title>

        <v-btn icon @click.stop="mini = !mini">
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item v-for="item in items" :key="item.title" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title @click="goTo(item.url)">{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <Nuxt />
    </v-main>
  </v-app>
</template>

<style scoped>
</style>

<script>
export default {
  head: {
    title: "Home"
  },
  data() {
    return {
      drawer: true,
      mini: false,
      items: [
        { title: "Home", icon: "mdi-home", url: "/dashboard" },
        {
          title: "Products",
          icon: "mdi-package-variant-closed",
          url: "/products"
        },
        { title: "Users", icon: "mdi-account-multiple", url: "/users" },
        { title: "Reports", icon: "mdi-poll", url: "/reports" },
        {
          title: "Preferences",
          icon: "mdi-account-settings",
          url: "/preferences"
        }
      ],
      items2: [{ picture: 28, name: "Joseph" }]
    };
  },
  methods: {
    goTo(url) {
      this.$router.push(url);
    }
  }
};
</script>
