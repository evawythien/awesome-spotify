<template>
  <footer :class="{'footer--right': !linksEnabled}">
    <link-number
      :show="linksEnabled"
      :show-previous-page="previousPage > 0"
      :to-previous="`${pageRoot}${previousPage}`"
      :show-next-page="nextPage > 0"
      :to-next="`${pageRoot}${nextPage}`"
      :current-page="currentPageInt"
      :total-pages="numberedPages"
    />

    <link-next :show="linksEnabled && !isLastPage" :to="`${pageRoot}${nextPage}`"/>

    <footer-nav />
  </footer>
</template>

<script>

import menunumber from '~/components/menunumber.vue';
import linkmenu from '~/components/linkmenu.vue';
import footernavigation from '~/components/footernavigation.vue';

export default {
    components: {
        menunumber,
        linkmenu,
        footernavigation,
    },
    data() {
        return {
            currentPage: 1,
            numberedPages: 2,
            linksEnabled: false,
            isLastPage: false,
            previousPage: 0,
            nextPage: 0,
            pageRoot: 'music-',
        };
    },
    computed: {
        currentPageInt() {
            return parseInt(this.currentPage, 10);
        },
    },
    watch: {
        $route: 'routeChanged',
    },
    created() {
        this.routeChanged();
    },
    methods: {
      
        routeChanged() {
            const routePath = this.$route.path;

            this.setLinksEnabled(routePath);
            this.setPagesVariables(routePath);
        },

        setLinksEnabled(routePath) {
            this.linksEnabled = (routePath !== '/');
        },

        setPagesVariables(routePath) {
            if (this.linksEnabled && routePath) {
                [, this.currentPage] = routePath.split(this.pageRoot);
                this.setPreviousNextPage();
                this.setIsLastPage();
            }
        },

        setIsLastPage() {
            this.isLastPage = (this.currentPageInt === this.numberedPages);
        },

        setPreviousNextPage() {
            this.previousPage = 0;
            this.nextPage = 0;

            if (this.currentPageInt === this.numberedPages) {
                this.previousPage = this.currentPageInt - 1;
            } else if (this.currentPageInt === 1) {
                this.nextPage = this.currentPageInt + 1;
            }
        },
    },
};
</script>

<style>
     footer {
          display: flex;
          justify-content: space-between;
          align-items: center;
          padding: 0 2rem;
     }

     footer.footer--right {
          justify-content: flex-end;
     }
     
</style>