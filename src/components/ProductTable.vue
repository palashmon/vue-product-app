<template>
  <div class="content-body" v-cloak>
    <table class="table table-sm table-hover">
      <thead class="thead-light">
        <tr>
          <th>Name</th>
          <th>Price</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="row in filteredProducts">
          <ProductRow v-if="row.isProductRow" :product="row.product" :key="row.product.id"/>
          <ProductCategoryRow v-else :category="row.product.category" :key="row.product.category"/>
        </template>
      </tbody>
    </table>
  </div>
</template>

<script>
import ProductRow from './ProductRow';
import ProductCategoryRow from './ProductCategoryRow';

export default {
  name: 'ProductTable',
  props: ['filterText', 'inStockOnly', 'products'],
  components: {
    ProductRow,
    ProductCategoryRow,
  },

  // computed properties
  // http://vuejs.org/guide/computed.html
  computed: {
    filteredProducts() {
      let lastCategory = null;
      const rows = [];

      this.products.forEach((product) => {
        if (
          product.name.toLowerCase().indexOf(this.filterText.toLowerCase())
          === -1
        ) {
          return;
        }
        if (this.inStockOnly && !product.stocked) {
          return;
        }
        if (product.category !== lastCategory) {
          rows.push({
            isProductRow: false,
            product,
          });
        }
        rows.push({
          isProductRow: true,
          product,
        });
        lastCategory = product.category;
      });

      return rows;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
[v-cloak] {
  display: none;
}
</style>
