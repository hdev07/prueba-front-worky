<template>
  <div>
    <v-card class="mx-4">
      <div class="text-overline m-4">Users - La Mas Exitosa</div>
    </v-card>
    <div class="pt-2 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
      <div v-for="item in users.users" :key="item.id">
        <v-card class="m-4">
          <v-card-text>
            <p class="text-h4 text--primary">{{ item ? item.firstName : '' }} {{ item ? item.lastName : ''}}</p>
            <div>{{ item ? item.username : '' }}</div>
            <div class="flex justify-between">
              <p>Gender: {{ item ? item.gender : '' }}</p>
              <p>Age: {{ item ? item.age : '' }}</p>
            </div>
            <div class="flex justify-between">
              <p>{{ item ? item.email : '' }}</p>
              <p>{{ item ? item.phone : '' }}</p>
            </div>
          </v-card-text>
        </v-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: "auth",
  data() {
    return {  users: [], reveal: false };
  },
  async fetch() {
    try {
      await fetch('https://dummyjson.com/users')
        .then(res => res.json())
        .then(data => {
          this.users = data;
        });
    } catch (error) {
      console.error(error);
    }
  }
};
</script>

<style>
.v-card--reveal {
  bottom: 0;
  opacity: 1 !important;
  position: absolute;
  width: 100%;
}
</style>
