<template>
  <div>
    <p ref="playing_now"></p>
  </div>
</template>

<script>
export default {
  methods: {
    /* printing the name of the song*/
    music_playing_now(name) {
        /* printing the name of the chosen song to be added to the playing now  */
      this.$refs[`playing_now`][`innerHTML`] = name;
    },
  },
  mounted() {
    this.$root.$on(`music_playing_clicked`, this.music_playing_now);
  },
  data() {
    return {
      now_playing_in_on: false,
    };
  },
};
</script>

<style scoped></style>