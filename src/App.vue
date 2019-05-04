<template>
  <div id="app">
    <FilterableProductTable :products="products"/>
  </div>
</template>

<script>
import JsonApi from './api';
import FilterableProductTable from '@/components/FilterableProductTable';

export default {
  name: 'app',
  components: {
    FilterableProductTable,
  },
  data() {
    return {
      products: JsonApi.getAllProducts(),
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
