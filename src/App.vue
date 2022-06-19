<template>
  <div class="app-container p-3 bg-black m-auto">
    <SongList></SongList>
  </div>
</template>

<script>
  import SongList from "./components/songList.vue";
  export default {
    name: "App",
    components: {
      SongList,
    },
  };
</script>

<style lang="scss">
  .app-container {
    width: 350px;
    height: 850px;
  }
  
</style>
