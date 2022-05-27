<template>
  <div>
    <apexchart 
      :type="type" 
      :options="options" 
      :series="series"
      width="100%" 
      height="280"
    />
  </div>
</template>
<script>
export default {
  name: "apexcharts",

  props: {
    type: { type: String, default: 'area' },
    series: { type: Array, default: () => [] },
    options: { type: Object, default: () => ({}) },
  },
};
</script>
<style scoped>
</style>