<template>
  <main class="my-successlist">
    <h1>Listas de éxitos</h1>
    <section class="my-successlist-section">
      <img :src="topArtistImage" class="my-successlist-section__image">
      <div class="my-successlist-section__list">
        <p>Como tu playlist, ninguna.</p>
        <p>Tus artistas favoritos y las canciones más escuchadas el último mes.</p>
        <div class="my-successlist-section__artists-songs">
          <div class="my-successlist-section__list--artists">
            <p>ARTISTAS FAVORITOS</p>
            <ul>
              <li v-for="artist in artists.items" :key="artist.name">
                <span class="fas fa-genderless"> {{ artist.name }} </span>
              </li>
            </ul>
          </div>
          <div class="my-successlist-section__list--songs">
            <p>CANCIONES FAVORITAS</p>
            <ul>
              <li v-for="track in tracks.items" :key="track.name">
                <span class="fas fa-genderless"> {{ track.name }} </span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import { setSpotifyAccessToken, getArtists, getTracks } from '~/code/spotify';

export default {
  head() {
    return {
      title: 'Listas de éxitos',
        meta: [
          {
          hid: 'description',
          name: 'description',
          content: 'La lista de los artistas y las canciones que más has escuchado en Spotify.'
          },
        ],
      };
    },
    async asyncData() {
      await setSpotifyAccessToken();
    
      const { artists, topArtistImage } = await getArtists('medium_term');
      const { tracks } = await getTracks('medium_term');
      return { artists, topArtistImage, tracks };
    },
};
</script>

<style scoped>

main {
    background-color: #ffc965;
}

h1 {
    font-size: 7.5em;
    text-align: center;
    margin-top: 4rem;
}

.my-successlist-section {
    display: flex;
    justify-content: center;
    align-items: center;
}

.my-successlist-section__image {
    max-width: 300px;
}

.my-successlist-section__list {
    margin-left: 2rem;
    font-size: 1.2em;
}

.my-successlist-section__list > p {
    margin-bottom: 1rem;
}

.my-successlist-section__list ul {
    padding: 0;
    list-style-type: none;
}

.my-successlist-section__artists-songs {
    display: flex;
    justify-content: space-between;
}

.my-successlist-section__list--artists {
    margin-right: 2rem;
}

.my-successlist-section__list--artists p, .my-successlist-section__list--songs p {
    font-weight: 600;
    margin-bottom: 1rem;
}
</style>