<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
    </div>
</template>

<script>
    import axios from 'axios';
    import SearchBar from './components/SearchBar';
    import VideoList from './components/VideoList';
    import keys from '../config/keys';
    
    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList
        },
        data() {
            return { videos: [] };
        },
        methods: {
            onTermChange(searchTerm) {
                axios.get(`https://www.googleapis.com/youtube/v3/search`, {
                    params: {
                        key: keys.API_KEY,
                        type: 'video',
                        part: 'snippet',
                        q: searchTerm
                    }
                }).then(response => {
                    this.videos = response.data.items;
                });
            },
            onVideoSelect(video) {
                console.log(video.snippet.title);
            }
        }
    }
</script>

<style>

</style>

