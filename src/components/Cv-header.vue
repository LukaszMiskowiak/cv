<template>
  <header v-if="src.ready">
    <h2>{{src.name}}</h2>
    <h2>{{src.position}}</h2>
    <ul>
      <li v-for="(p, i) in src.personalInfo" :key="i">
        {{p}}
      </li>
    </ul>
  </header>
</template>

<script>
export default {
    name: 'cvHeader',
    props: ['src'],
};
</script>

<style lang="scss" scoped>

</style>
