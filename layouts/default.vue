<template>
  <div class="container">
    <theheader :background-color="backgroundColor" />
    <nuxt/>
    <thefooter :background-color="backgroundColor" />
  </div>
</template>

<script>
import theheader from '~/components/theheader.vue';
import thefooter from '~/components/thefooter.vue';
export default {
    components: {
        theheader,
        thefooter,
    },
    data() {
        return {
            backgroundColor: '#fff',
        };
    },
    watch: {
        $route: 'routeChanged',
    },
    created() {
        this.routeChanged();
    },
    methods: {
        /* Solution from conditional logic issue:
        https://github.com/nuxt/nuxt.js/issues/180
        */
        routeChanged() {
            this.setBackgroundColor();
        },

        setBackgroundColor() {
            const routePath = this.$route.path;
            const pageRoot = 'my-music-';
            const [, currentPage] = routePath.split(pageRoot);
            const backgroundList = ['#638de8', '#ffc965', '#b79cc9'];
            const isPage = [routePath === '/', currentPage === '1', currentPage === '2'];

            isPage.forEach((isPageItem, index) => {
                if (isPageItem) {
                    this.backgroundColor = backgroundList[index];
                }
            });
        },
    },
};
</script>

<style>
</style>

AAAAAAAAAAAAA