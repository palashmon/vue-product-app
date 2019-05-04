<template>
  <tr>
    <td>
      <span class="pl-4" :class="{ 'red': !product.stocked }">{{product.name}}</span>
    </td>
    <td>{{product.price}}</td>
  </tr>
</template>

<script>
export default {
  name: 'ProductRow',
  props: ['product'],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.red {
  color: #dc3545;
}
</style>
