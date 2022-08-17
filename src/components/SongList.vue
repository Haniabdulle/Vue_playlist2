<template>
  <div>
    <section>
      <article v-for="song in songs" :key="song[`song_id`]">
          <p>{{ song[`title`] }}</p>
          <p>{{ song[`artist`] }}</p>
          <img
            :src="song[`img_url`]"
            alt=""
            @click="highlight_music"
            :song_id="song[`song_id`]"
          />
      </article>
    </section>
    <div v-if="song_being_listened === false">
      <h2>Add the songs for your playlist</h2>
    </div>
    <div v-else>
      <h1>Playlist</h1>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    /* button click */
    highlight_music(details) {
    let song_id = details[`target`].getAttribute(`song_id`);    /* Song id*/
      this.song_being_listened = true;
      details[`target`].remove();          /* deleting the img so the user can't add twice or more the same music */
      for (let i = 0; i < this.songs.length; i++) {
        /* checking if the song id in the i position matches to the song id of the clicked img */
        if (this.songs[i][`song_id`] === song_id) {
          /* Grabbing all the information of the music */
          let chosen_music_object = this.songs[i];
          this.$root.$emit(`music_clicked`, chosen_music_object); 
        }
      }
    },
  },
  data() {
    return {
      song_being_listened: false,
      songs: [
        {
          title: `Proud of myself`,
          artist: `YoungBoy `,
          song_id: `10`,
          img_url:  ` https://i.scdn.co/image/ab67616d0000b2736fff08fad874ee9936489d09   `,
        },
        {
          title: `Fire and desire`,
          artist: `Drake`,
          song_id: `20`,
          img_url: `https://i1.sndcdn.com/artworks-Z19d1jdImMbt-0-t500x500.jpg`,
        },
        {
          title: `Keeper`,
          artist: `Toosii`,
          song_id: `30`,
          img_url: ` https://i1.sndcdn.com/artworks-yttGkz8AYKPb-0-t500x500.jpg `,
   },
      ],
    };
  },
};
</script>

<style scoped>
section {
  grid-template-columns: 1fr 1fr 1fr;
  display: grid
  
}
img {
  width: 200px;
  height: 200px;
}
</style>