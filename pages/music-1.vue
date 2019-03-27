<script>
import { setSpotifyAccessToken, getArtists, getTracks, } from '~/code/spotify';

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