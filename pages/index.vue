<template>
  <main class="index">
    <h1>Tu música en resumen.</h1>
    <div class="musicLink">
      <nuxt-link to="/successlist">Conecta con Spotify</nuxt-link>
    </div>
  </main>
</template>

<style scoped>

  main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #fff;
  }

  h1 {
    font-size: 7.5em;
    max-width: 60%;
    text-align: center;
    color: #B6E8AA;
  }

  .musicLink {
    margin-top: 2.5rem;
  }

  .musicLink a {
    text-transform: uppercase;
    font-weight: 600;
    text-decoration: none;
    background: rgba(182, 232, 227, 1);
    color: #0a0a0a;
    border: 1px solid #4e57ef;
    box-shadow: 7px 7px 0px #4e57ef;
    padding: 20px;
  }

</style>