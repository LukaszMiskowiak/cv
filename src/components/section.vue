<template>
  <section>
    <h1>{{data.h1}}</h1>
    <div v-for="(p, i) in paragraphs" :key="`item-${i}`">
      <p v-for="(text, key) in p.children" :key="`p-${key}`">
        {{text.text}}
      </p>
    </div>
    <div v-for="(ul, i) in lists" :key="`list-${i}`">
      <ul>
        <div v-for="(li, key) in ul" :key="`item-${key}`">
          <li v-if="li.children.length > 1">
            <span v-for="(c, index) in li.children" :key="`list-${key}-content-${index}`">
              {{c.text}}
            </span>
          </li>
          <li v-else>
            {{li.children[0].text}}
          </li>
        </div>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
    name: 'section_cv',
    computed: {
        paragraphs() {
            const p = [];
            this.data.article.forEach((a) => {
                if (!a.listItem) p.push(a);
            });
            return p;
        },
        lists() {
            const ul = [];
            let li = [];
            this.data.article.forEach((a) => {
                if (a.listItem) li.push(a);
                if (!a.children[0].text) {
                    ul.push(li);
                    li = [];
                };
            });
            if (li.length) ul.push(li);
            return ul;
        },
    },
    props: ['data'],
};
</script>

<style scoped>

</style>
