<template>
    <div v-if="show" class="footer-link-next">
        <nuxt-link :to="to" class="footer-link-next__link">
            <span class="fas fa-2x fa-angle-double-down"/>
        </nuxt-link>
    </div>
</template>

<script>
export default {
    props: {
        show: {
            type: Boolean,
            required: true,
        },
        to: {
            type: String,
            required: true,
        },
    },
};
</script>
