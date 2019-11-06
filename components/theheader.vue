<template>
  <header :style="{ backgroundColor: backgroundColor }">
    <div class="logo">
      <a href="/"><img  src="~assets/images/spotify-logo.svg" ></a>
    </div>
  </header>
</template>

<script>
export default {
    props: {
        backgroundColor: {
            type: String,
            required: false,
            default: '#fff',
        },
    },
};
</script>

<style>
header {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.logo {
  margin-left: 4rem;
  margin-top: 2rem;
}

.logo img { 
  width: 70px; 
}
</style>