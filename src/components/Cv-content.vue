<template>
  <section>
    <h2>{{src.title}}</h2>
    <p>{{src.text}}</p>
    <ul  v-for="(li, i) in src.list" :key="i">
      <h3>{{li.title}}</h3>
      <li v-for="(item, i) in li.items" :key="i">
        <div v-if="typeof item === 'string'">
          {{item}}
        </div>
        <div v-else-if="typeof item === 'object'">
          <p v-if="item.type === 'p'">{{item.text}}</p>
          <span v-else-if="item.type === 'span'">{{item.text}}</span>
          <p v-else-if="item.type === 'date'">{{item.text}}</p>
        </div>
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
