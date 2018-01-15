<template>
  <footer v-if="src.ready">
    <h2>{{src.title}}</h2>
    <p>{{src.clause}}</p>
  </footer>
</template>

<script>
export default {
    name: 'cvFooter',
    props: ['src'],
};
</script>

<style scoped>

</style>
