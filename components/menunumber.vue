<template>
    <div v-if="show" class="footer-link-number">
        <nuxt-link v-if="showPreviousPage" :to="toPrevious" class="fas fa-angle-up"/>
        <span>{{ currentPage }} / {{ totalPages }}</span>
        <nuxt-link v-if="showNextPage" :to="toNext" class="fas fa-angle-down"/>
    </div>
</template>

<script>

export default {
    props: {
        show: {
            type: Boolean,
            required: true,
        },
        showPreviousPage: {
            type: Boolean,
            required: true,
        },
        toPrevious: {
            type: String,
            required: true,
        },
        showNextPage: {
            type: Boolean,
            required: true,
        },
        toNext: {
            type: String,
            required: true,
        },
        currentPage: {
            type: Number,
            required: true,
        },
        totalPages: {
            type: Number,
            required: true,
        },
    },
};
</script>
