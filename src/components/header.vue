<template>
  <header>
    <div v-for="(text, i) in headers" :key="`header-${i}`">
      <h1 v-if="text.style === 'h1'">{{text.children[0].text}}</h1>
      <h2 v-else-if="text.style === 'h2'">{{text.children[0].text}}</h2>
    </div>
    <div v-for="(item, i) in list" :key="`list-${i}`">
      <ul>
        <li v-for="(text, key) in item.children" :key="`li-${key}`" v-if="text.text">
          <a v-if="item.markDefs.length && item.markDefs[0].href" :href="item.markDefs[0].href">
            {{text.text}}
          </a>
          <span v-else>{{text.text}}</span>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
export default {
    name: 'header_cv',
    computed: {
        headers() {
            return this.data.filter(t => t.style !== 'normal');
        },
        list() {
            return this.data.filter(t => t.listItem === 'bullet');
        },
    },
    props: ['data'],
};
</script>

<style scoped>

</style>
