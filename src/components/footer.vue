<template>
  <footer>
    <div v-for="(text, i) in data" :key="`footer-${i}`">
      <p>{{text.children[0].text}}</p>
    </div>
  </footer>
</template>

<script>
export default {
    name: 'footer_cv',
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
