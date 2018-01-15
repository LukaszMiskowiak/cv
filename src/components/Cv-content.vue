<template>
  <section v-if="src.ready">
    <h2>{{src.title}}</h2>
    <p>{{src.text}}</p>
    <ul  v-for="(li, i) in src.list" :key="i">
      <h3>{{li.title}}</h3>
      <li v-for="(text, i) in li.items" :key="i">
        {{i}}
      </li>
    </ul>
  </section>
</template>

<script>
export default {
    name: 'cvContent',
    props: ['src'],
};
</script>

<style scoped>

</style>
