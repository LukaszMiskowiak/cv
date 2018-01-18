<template>
  <header>
    <div class="header">
      <span v-for="(text, i) in headers" :key="`header-${i}`">
        <h1 v-if="text.style === 'h1'">{{text.children[0].text}}</h1>
        <h2 v-else-if="text.style === 'h2'">{{text.children[0].text}}</h2>
      </span>
    </div>
    <div v-for="(ul, i) in lists" :key="`list-${i}`">
      <ul>
        <div v-for="(li, key) in ul" :key="`item-${key}`">
          <li v-if="li.children.length > 1">
            <span v-for="(c, index) in li.children" :key="`list-${key}-content-${index}`">
              <a v-if="li.markDefs.length" href="li.markDefs[0].href">
                {{c.text}}
              </a>
              <span v-else>
                {{c.text}}
              </span>
            </span>
          </li>
          <li v-else>
            {{li.children[0].text}}
          </li>
        </div>
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
        lists() {
            const ul = [];
            let li = [];
            this.data.forEach((a) => {
                if (a.listItem) li.push(a);
                if (!a.children[0].text) {
                    ul.push(li);
                    li = [];
                }
            });
            if (li.length) ul.push(li);
            return ul;
            // return this.data.filter(t => t.listItem === 'bullet');
        },
    },
    props: ['data'],
};
</script>

<style lang="scss" scoped>

  header {
    .header {
      display: flex;
      flex-direction: row;
      h1, h2 {
        display: block;
        padding-right: 1rem;
      }
    }
    ul {
      list-style: none;
      display: flex;
      margin: auto;
      justify-content: space-between;
      flex-direction: row;
      margin: 0;
      padding: 0;
      li {
        display: block;
        font-size: .87rem;
      }
    }
  }

</style>
