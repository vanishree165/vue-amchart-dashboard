<template>
  <div id="app">
    <StockChart />
    <LineChart />
  </div>
</template>

<script>
import StockChart from "./components/StockChart.vue";

export default {
  name: "App",
  components: {
    StockChart,
  },
};
</script>

<style>
/* Add your global styles here */
</style>
