<template>
  <main class="index">
    <h1>
      Tu música en resumen.
    </h1>
    <div class="index__link">
      <nuxt-link to="/music-1">
        Conecta con Spotify
      </nuxt-link>
    </div>
  </main>
</template>

<style scoped>

main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #638de8;
}

h1 {
  font-size: 7.5em;
  max-width: 60%;
  text-align: center;
  color: #d4f9f4;
}

.index__link {
  margin-top: 2.5rem;
}

.index__link a {
  text-transform: uppercase;
  font-weight: 600;
  text-decoration: none;
  background-color: #d4f9f4;
  color: #638de8;
  padding: 1.2rem;
  border-radius: 2rem;
}

</style>

<script>
export default {
  head() {
    return {
      title: 'Tu música en resumen',
        meta: [       
          { hid: 'description', name: 'description', content: 'Descubre tus artistas y canciones favoritos en Wecodefy.' },     
      ],
    };
  },
};
</script>