<template>
  <section :class="data.h1.split(' ')[0].toLowerCase()">
    <h1>{{data.h1}}</h1>
    <div v-for="(p, i) in paragraphs" :key="`item-${i}`">
      <p v-for="(text, key) in p.children" :key="`p-${key}`">
        <i v-if="text.marks.length && !p.isLink">{{text.text}}</i>
        <a v-else-if="p.isLink" href="text.text">{{text.text}}</a>
        <span v-else>
          {{text.text}}
        </span>
      </p>
    </div>
    <div class="lists">
      <ul v-for="(ul, i) in lists" :key="`list-${i}`" >
        <div v-for="(li, key) in ul" :key="`item-${key}`">
          <li v-if="li.children.length > 1">
            <div v-for="(c, index) in li.children" :key="`list-${key}-content-${index}`">
              <b v-if="c.marks.length">{{c.text}}</b>
              <span v-else>
                {{c.text}}
              </span>
            </div>
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
                if (!a.listItem && a.children[0].text) p.push(a);
                if (a.markDefs.length && a.children.length > 1) {
                    const link = a;
                    link.children = [a.children[1]];
                    link.isLink = true;
                    p.push(link);
                }
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
                }
            });
            if (li.length) ul.push(li);
            return ul;
        },
    },
    props: ['data'],
};
</script>

<style lang="scss" scoped>

  .technology {
    .lists {
      display: flex;
      flex-direction: column;
      justify-content: center;
      > ul {
        list-style: none;
        display: flex;
        flex-direction: row;
        justify-content: center;
        margin: 0;
        padding: 0;
        li {
          padding-right: .5rem;
          font-weight: 600;
        }
      }
    }
  }

  .experience {
    p {
      text-align: center;
    }
  }

</style>
