<template>
  <div id="app">
    <song-list></song-list>
    <play-list></play-list>
    <now-playing></now-playing>
  </div>
</template>

<script>
import NowPlaying from './components/NowPlaying.vue';
import PlayList from "./components/PlayList.vue";
import SongList from "./components/SongList.vue";
export default {
  name: "App",
  components: {
    SongList,
    PlayList,
    NowPlaying,
  },
};
</script>

<style>

</style>
