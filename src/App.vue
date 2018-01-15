<template>
  <main id="app" class="A5">
    <article class="sheet padding-10mm cv">
      <cvHeader :src="header" />
      <cvContent v-for="(c, i) in content" :key="`c-${i}`" :src="c" />
      <cvFooter :src="footer" />
    </article>
  </main>
</template>

<script>
import cvHeader from './components/Cv-header';
import cvContent from './components/Cv-content';
import cvFooter from './components/Cv-footer';

require('../node_modules/paper-css/paper.min.css');

export default {
    name: 'App',
    data() {
        return {
            header: [],
            content: [],
            footer: [],
        };
    },
    components: {
        cvHeader,
        cvContent,
        cvFooter,
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
