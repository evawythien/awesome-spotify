<script>
import {
    setSpotifyAccessToken, getArtists, getTracks, getTopGenre,
} from '~/code/spotify';

export default {
    head() {
        return {
            title: 'Comparte tu música',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'Comparte tus artistas y canciones favoritos de Wecodefy.',
                },
                { 
                    name: 'twitter:title',
                    content: 'Wecodefy', 
                },
                {
                    name: 'twitter:description',
                    content: 'Descubre tus artistas y canciones favoritos de Wecodefy',
                },
                {
                    name: 'twitter:image',
                    content: '~assets/images/wecodefy-logo.png',
                },
                { 
                    name: 'twitter:card', 
                    content: 'summary_large_image', 
                },
            ],
            link: [
                {
                    rel: 'canonical',
                    href: 'https://github.com/evawythien/awesome-spotify',
                },
            ],
        };
    },
    async asyncData() {
        await setSpotifyAccessToken();
        // data since last years
        const { artists, topArtistImage } = await getArtists('long_term');
        const { tracks } = await getTracks('long_term');
        const topGenre = getTopGenre(artists);
        return {
            artists, topArtistImage, tracks, topGenre,
        };
    },
};
</script>