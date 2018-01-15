<template>
  <main id="app" class="A5">
    <article class="sheet padding-10mm cv">
      <cvHeader v-if="header.ready" :src="header" />
      <cvContent v-if="content.ready" v-for="(c, i) in content.content" :key="`c-${i}`" :src="c" />
      <cvFooter v-if="footer.ready" :src="footer" />
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
            header: {
                name: 'Łukasz Miśkowiak',
                position: 'JavaScript Developer',
                personalInfo: [
                    'lukaszmiskowiak@gmail.com',
                    '732012811',
                    'Sopot, Poland',
                    'github.com/lukaszmiskowiak',
                ],
                ready: true,
            },
            content: {
                content: [
                    {
                        title: 'Technology Stack',
                        text: '',
                        list: [
                            {
                                title: '',
                                items: ['JavaScript', 'ES3', 'ES5', 'ES6', 'Node.js'],
                            },
                            {
                                title: '',
                                items: ['HTML5', 'CSS3', 'SASS', 'SQL'],
                            },
                            {
                                title: '',
                                items: ['Vue.js', 'Vuex', 'React.js', 'Redux'],
                            },
                            {
                                title: '',
                                items: ['Sanity (headles CMS)', 'Bootstrap', 'Npm', 'Yarn', 'Webpack', 'Babel', 'ESLint', 'Git'],
                            },
                        ],
                    },
                    {
                        title: 'Sample Projects',
                        text: '',
                        list: [
                            {
                                title: 'cli templates',
                                items: [
                                    {
                                        text: 'A cli Tool for the purpouse of creating templates',
                                        type: 'p',
                                    },
                                    {
                                        text: 'Choose among templates and components to create web application',
                                        type: 'p',
                                    },
                                    {
                                        text: 'Node.js (inquirer, fs)',
                                        type: 'span',
                                    },
                                    {
                                        text: 'january 2018',
                                        type: 'date',
                                    },
                                ],
                            },
                            {
                                title: 'Performance Review Tool',
                                items: [
                                    {
                                        text: 'An Application for creating their performance review document',
                                        type: 'p',
                                    },
                                    {
                                        text: 'Worker\'s performance review has categories with items. Items can be added at the start of the year, in the midlle of the year and at the end of the year. Each item can be accesed by user\' teamleader (using proper interface) and commented by him/her.',
                                        type: 'p',
                                    },
                                    {
                                        text: 'Node.js (Express)',
                                        type: 'span',
                                    },
                                    {
                                        text: 'Vue.js',
                                        type: 'span',
                                    },
                                    {
                                        text: 'Vuex',
                                        type: 'span',
                                    },
                                    {
                                        text: 'MySQL',
                                        type: 'span',
                                    },
                                    {
                                        text: 'september 2017 till december 2017',
                                        type: 'date',
                                    },
                                ],
                            },
                        ],
                    },
                    {
                        title: '',
                        text: '',
                        list: [
                            {
                                title: '',
                                items: [],
                            },
                        ],
                    },
                ],
                ready: true,
            },
            footer: {
                title: '',
                clause: '',
                ready: false,
            },
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
