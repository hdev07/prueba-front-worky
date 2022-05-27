<template>
  <div class="mx-4">
    <v-card>
      <div class="text-overline m-4">Details - {{ item ? item.title : ''}}</div>
    </v-card>
    <v-card class="mt-2" outlined>
      <v-list-item three-line>
        <v-list-item-content>
          <div class="text-overline mb-4">Brand: {{ item ? item.brand : '' }}</div>
          <v-list-item-title class="text-h5 mb-1">{{ item ? item.title : '' }}</v-list-item-title>
          <v-list-item-subtitle>{{ item ? item.description : '' }}</v-list-item-subtitle>
          <v-list-item-subtitle>{{ item ? item.category : '' }}</v-list-item-subtitle>
        </v-list-item-content>

        <v-list-item-avatar tile size="150" color="grey">
          <img :src="item ? item.thumbnail : ''" alt="item" />
        </v-list-item-avatar>
      </v-list-item>

      <v-card-actions class="flex justify-between m-2">
        <div class="flex">
          <v-rating
            :value="item ? item.rating : ''"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          />
          <div class="grey--text ms-4">{{ item ? item.rating : '' }}</div>
        </div>
        <span>Price - $ {{ item ? item.price : '' }}</span>
      </v-card-actions>
    </v-card>
    <v-carousel v-model="model" class="mt-2">
      <v-carousel-item v-for="(image, i) in item.images" :key="i">
        <v-sheet height="100%" tile>
          <v-row class="fill-height" align="center" justify="center">
            <div class="text-h5">
              <img :src="image" alt />
            </div>
          </v-row>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  layout: "auth",

  asyncData({ params }) {
    return {
      productId: params.id
    };
  },

  data() {
    return {
      item: {},
      model: 0
    };
  },

  async fetch() {
    try {
      await fetch(`https://dummyjson.com/products/${this.productId}`)
        .then(res => res.json())
        .then(data => {
          this.item = data;
        });
    } catch (e) {
      console.error(e);
    }
  },
  methods: {}
};
</script>

<style>
</style>