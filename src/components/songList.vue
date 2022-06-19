<template>
  <div>
    <div v-if="!isPlayerVisible">
      <div class="text-yellow-300 font-bold text-center text-3xl mb-7 mt-3">
        VueJs Music App
      </div>
      <div
        v-for="(song, songx) in list"
        :key="song.id"
        class="flex flex-row justify-between mb-4 cursor-pointer"
        @click="playSong(songx)"
      >
        <div>
          <span class="text-yellow-400">{{ song.name }}</span
          ><br />
          <span class="text-gray-200 text-xs"
            >{{ song.artistName }} -
            <span class="text-gray-400"
              >{{ song.artistalbumName }} {{ song.year }}</span
            >
          </span>
        </div>
        <div>
          <img :src="song.src" class="max-h-12 rounded" alt="" />
        </div>
      </div>
    </div>

    <div v-if="isPlayerVisible">
      <song-player
        :song="list[currentSongIndex]"
        @goback="isPlayerVisible = !isPlayerVisible"
        @next="playNext"
        @previous="playPrevious"
      ></song-player>
    </div>
  </div>
</template>

<script>
  import SongPlayer from "./SongPlayer.vue";
  export default {
    name: "songList",
    components: {
      SongPlayer,
    },
    data() {
      return {
        isPlayerVisible: false,
        currentSongIndex: 0,
        list: [
          {
            id: 1,
            name: "Infinity",
            artistName: "Shwe Htoo",
            albumName: "Infinity",
            year: 2017,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require("../assets/mp3/Infinily (အဆံုးမဲ့) - Shwe Htoo (ေရႊထူး) 2017 New Song.mp3"),
          },
          //   {
          //     id: 2,
          //     name: "Lean on",
          //     artistName: "Adam Levine",
          //     albumName: "Goind Down",
          //     year: 2001,
          //     src: `https://source.unsplash.com/random/400x400?date=2`,
          //     songSrc: `https://filesamples.com/samples/audio/mp3/sample3.mp3`,
          //   },
          //   {
          //     id: 3,
          //     name: "Counting Stars",
          //     artistName: "Adam Hart",
          //     albumName: "Spice It Up",
          //     year: 2003,
          //     src: `https://source.unsplash.com/random/400x400?date=3`,
          //     songSrc: `https://filesamples.com/samples/audio/mp3/sample1.mp3`,
          //   },
          {
            id: 4,
            name: "Liar",
            artistName: "XBOX",
            albumName: "Liar",
            year: 2017,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require("../assets/mp3/XBOX - Liar.mp3"),
          },
          {
            id: 5,
            name: "Starry Night",
            artistName: "Big Bag",
            albumName: "Starry Night",
            year: 2017,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require("../assets/mp3/ရင္ဘတ္အနီးတ၀ုိက္ပတ္ပတ္လည္ နင္ဘယ္မွထြက္မသြားနဲ Big Bag-Starry Night.mp3"),
          },
          {
            id: 6,
            name: "Carbon Dioxide",
            artistName: "Hlwan Paing",
            albumName: "Carbon Dioxide",
            year: 2017,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require("../assets/mp3/Hlwan Paing - Carbon Dioxide.mp3"),
          },
          {
            id: 7,
            name: "Mine",
            artistName: "Bazzi",
            albumName: "Mine",
            year: 2019,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require("../assets/mp3/Bazzi - Mine (Official Video) - YouTube.mp3"),
          },
          {
            id: 8,
            name: "WOW",
            artistName: "Tiësto",
            albumName: "WOW",
            year: 2019,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require("../assets/mp3/Tiësto - WOW (Official Audio)_low.mp3"),
          },
          {
            id: 9,
            name: "တစ်ဖက်သတ်",
            artistName: "X-Box",
            albumName: "တစ်ဖက်သတ်",
            year: 2017,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require("../assets/mp3/X-Box  Myanmar New SONG 2016 တစ္ဖက္သတ္ (Ta Phat Thet) MTV.mp3"),
          },
          {
            id: 10,
            name: "Mujeriego_💋",
            artistName: "Ryan_Castro",
            albumName: "Mujeriego_💋",
            year: 2021,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require(`../assets/mp3/Ryan_Castro_-_Mujeriego_💋_(Vídeo_Oficial)(360p).mp4`),
          },
          {
            id: 11,
            name: "Restricted_Edit",
            artistName: "Captain",
            albumName: "Restricted_Edit",
            year: 2021,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require(`../assets/mp3/Captain_(Restricted_Edit)(360p).mp4`),
          },
          {
            id: 12,
            name: "Frozen_(Sickick_Remix)",
            artistName: "Madonna Vs Sickick",
            albumName: "Frozen_(Sickick_Remix)",
            year: 2021,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require(`../assets/mp3/Madonna_Vs._Sickick_-_Frozen_(Sickick_Remix)(360p).mp4`),
          },
          {
            id: 13,
            name: "Problem",
            artistName: "Ariana Grande",
            albumName: "Problem",
            year: 2022,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require(`../assets/mp3/Problem   Ariana Grande lyrics HQ AUDIO1_low.mp3`)},
          {
            id: 14,
            name: "ဆောင်း",
            artistName: "Double J",
            albumName: "ဆောင်း",
            year: 2021,
            src: `https://source.unsplash.com/random/400x400?date=1`,
            songSrc: require(`../assets/mp3/Facebook 670822316671782(720p).mp3`)},
        ],
      };
    },
    methods: {
      playSong(x) {
        this.currentSongIndex = x;
        this.isPlayerVisible = true;
      },
      playNext() {
        if (this.currentSongIndex < this.list.length - 1) {
          this.currentSongIndex += 1;
        } else {
          this.currentSongIndex = 0;
        }
      },
      playPrevious() {
        if (this.currentSongIndex != 0) {
          this.currentSongIndex -= 1;
        } else {
          this.currentSongIndex = this.list.length - 1;
        }
      },
    },
  };
</script>

<style lang="scss"></style>
