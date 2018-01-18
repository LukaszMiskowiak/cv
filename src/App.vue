<template>
  <main id="app" class="A5">
    <article class="sheet padding-10mm cv">

      <headerCv
        :data="data.header"
        v-if="ready"
      />
      <sectionCv
        v-for="(section, i) in data.section"
        :data="section"
        :key="`section-${i}`"
        v-if="ready"
      />
      <footerCv
        :data="data.footer"
        v-if="ready"
      />

    </article>
  </main>
</template>

<script>
import headerCv from './components/header';
import sectionCv from './components/section';
import footerCv from './components/footer';

require('../node_modules/paper-css/paper.min.css');

const sanityClient = require('@sanity/client');

const client = sanityClient({
    projectId: 'v43mmxg6',
    dataset: 'production',
    token: '',
    useCdn: true,
});

export default {
    name: 'App',
    data() {
        return {
            data: {},
            ready: false,
        };
    },
    beforeMount() {
        const query = '*[_type == "cv"] {header, footer, section[]->}[0]';
        client.fetch(query)
            .then((cv) => {
                this.data = cv;
                this.ready = true;
            });
    },
    components: {
        headerCv,
        sectionCv,
        footerCv,
    },
};
</script>

<style lang="scss">
/*$height: ;
$width: ;
$main-background-color: ;
$secondary-background-color:
$main-text-color: ;
$secondary-text-color: ;*/

.cv {

}
</style>
