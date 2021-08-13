<template>
  <v-container>
    <input-form
      formRounded="xl"
      :formElevation="formElevation"
      @storeMovie="showMovie"
    />

    <movies ref="movies" :movie-items="movieItems" />
  </v-container>
</template>

<script>
import InputForm from "./InputForm.vue";
import Movies from "./Movie.vue";
import axios from "axios";

export default {
  name: "Top",

  components: {
    InputForm,
    Movies,
  },

  data() {
    return {
      formElevation: "1",
      movieItems: [{}],
    };
  },

  created() {
    this.getMovies();
  },
  methods: {
    getMovies() {
      axios
        .get("https://youtube-curation.herokuapp.com/rest/1")
        .then((response) => {
          this.movieItems = response.data.user.movies;
        })
        .catch((error) => {
          console.log(error);
        })
        .finally(() => {
          this.$refs.movies.init();
        });
    },
    storeMovie(movieUrl, comment) {
      console.log(movieUrl, comment);
    },
  },
};
</script>

