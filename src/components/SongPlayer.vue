<template>
  <div class="text-white">
    <audio
      :src="song.songSrc"
      preload="auto"
      autoplay
      ref="audioPlayer"
    ></audio>
    <div class="text-white flex flex-row justify-between">
      <button @click="goback">Back</button>
      <div class="text-yellow-300 font-bold text-1xl">VueJs Music App</div>
    </div>
    <div>
      <img class="rounded mt-8 mb-4" :src="song.src" alt="" />
      <div class="text-center">
        <p class="text-yellow-300 font-bold">{{ song.name }}</p>
        <p class="text-gray-200">
          {{ song.artistName }} - {{ song.albumName }}
        </p>
        <p class="text-gray-400">{{ song.year }}</p>
      </div>
    </div>
    <div class="grid grid-cols-3 mt-10">
      <div class="flex item-center justify-center">
        <button @click="previous">Previous</button>
      </div>
      <div class="flex item-center justify-center">
        <button
          class="rounded-full bg-yellow-300 h-24 w-24 text-black font-bold"
          @click="togglePlay"
        >
          {{ isPlaying ? "pause" : "play" }}
        </button>
      </div>
      <div class="flex item-center justify-center">
        <button @click="next">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "SongPlayer",
    data() {
      return {
        isPlaying: true,
      };
    },
    props: {
      song: {
        id: Number,
        name: String,
        artistName: String,
        albumName: String,
        year: Number,
        src: String,
        songSrc: String,
      },
    },
    emit: ["goback", "next", "previous"],
    methods: {
      goback() {
        this.$emit("goback");
      },
      togglePlay() {
        if (this.isPlaying) {
          this.$refs.audioPlayer.pause();
        } else {
          this.$refs.audioPlayer.play();
        }
        this.isPlaying = !this.isPlaying;
      },
      next() {
        this.$emit("next");
      },
      previous() {
        this.$emit("previous");
      },
    },
  };
</script>

<style lang="scss"></style>
