<template>
  <div>
    <v-card class="mx-4">
      <div class="text-overline m-4">Products - La Mas Exitosa</div>
    </v-card>
    <div class="pt-2 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
      <div v-for="item in items.products" :key="item.id">
        <v-card class="m-4">
          <template slot="progress">
            <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
          </template>

          <v-img height="250" :src="item ? item.images[0] : ''"></v-img>

          <v-card-title>{{ item ? item.title : '' }}</v-card-title>

          <v-card-text>
            <v-row align="center" class="mx-0">
              <v-rating
                :value="item ? item.rating : ''"
                color="amber"
                dense
                half-increments
                readonly
                size="14"
              ></v-rating>

              <div class="grey--text ms-4">{{ item ? item.rating : '' }}</div>
            </v-row>

            <div class="my-4 text-subtitle-1">{{ item ? item.brand : '' }}</div>

            <div>{{ item ? item.description : '' }}</div>
          </v-card-text>

          <v-divider class="mx-4"></v-divider>

          <v-card-actions class="flex justify-between">
            <v-btn color="secondary" utlined text @click="details(item)">Details</v-btn>

            <span>In Stok - {{ item ? item.stock : '' }}</span>
          </v-card-actions>
        </v-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: "auth",
  data() {
    return {
      items: []
    };
  },

  async fetch() {
    try {
      await fetch("https://dummyjson.com/products")
        .then(res => res.json())
        .then(data => {
          this.items = data;
        });
    } catch (error) {
      console.error(error);
    }
  },
  methods: {
    details(item) {
      this.$router.push({ name: "products-id", params: { id: item.id } });
    }
  }
};
</script>

<style>
</style>