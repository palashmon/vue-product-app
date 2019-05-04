<template>
  <div class="container shadow-lg p-4 mb-4">
    <div class="pb-2 mt-4 mb-4 border-bottom">
      <h1>Simple Product Table</h1>
    </div>
    <div class="content-main">
      <SearchBar
        :filterText="filterText"
        :inStockOnly="inStockOnly"
        @inStockChanged="onInStockChanged"
        @filterTextChanged="onTextChange"
      />
      <ProductTable :products="products" :filterText="filterText" :inStockOnly="inStockOnly"/>
    </div>
  </div>
</template>

<script>
import SearchBar from './SearchBar';
import ProductTable from './ProductTable';

export default {
  name: 'FilterableProductTable',
  props: ['products'],
  components: {
    SearchBar,
    ProductTable,
  },
  data() {
    return {
      filterText: '',
      inStockOnly: false,
    };
  },
  methods: {
    onTextChange(value) {
      this.filterText = value;
    },
    onInStockChanged(value) {
      this.inStockOnly = value;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  max-width: 750px;
}
</style>
