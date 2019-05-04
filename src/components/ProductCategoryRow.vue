<template>
  <tr>
    <th colspan="2" class="text-success text-uppercase">{{ category }}</th>
  </tr>
</template>

<script>
export default {
  name: 'ProductCategoryRow',
  props: ['category'],
};
</script>
