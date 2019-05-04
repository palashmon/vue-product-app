<template>
  <div class="content-header">
    <div class="content-info">
      <form>
        <input
          type="text"
          placeholder="Search..."
          class="form-control input-block mb-2"
          autofocus
          autocomplete="off"
          @change="onTextChange"
        >
        <p class="mb-5">
          <input type="checkbox" @change="onInStockChange"> Only show
          products in stock
        </p>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  props: ['filterText', 'inStockOnly'],
  data() {
    return {
      rows: [],
    };
  },
  methods: {
    onTextChange(e) {
      this.$emit('filterTextChanged', e.target.value);
    },
    onInStockChange(e) {
      this.$emit('inStockChanged', e.target.checked);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
