<template>
  <v-row>
    <v-col
      v-for="item in movieInternalItems"
      :key="item.id"
      cols="12"
      sm="6"
      md="4"
      style="text-align: center"
    >
      <div>
        <iframe :src="item.url" width="290" height="163.125" frameborder="0" />
        <p>{{ item.comment }}</p>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  props: {
    movieItems: {
      type: Array,
      default: null,
    },
  },

  data() {
    return {
      movieInternalItems: [],
    };
  },

  methods: {
    init() {
      this.movieInternalItems = [];
      Object.keys(this.movieItems).forEach((i) => {
        console.log(this.movieItems[1]);
        const newItem = {
          id: this.movieItems[i].id,
          url:
            "https://www.youtube.com/embed/" +
            this.movieItems[1].url +
            "?controls=1&loop=1&playlist=",
          comment: this.movieItems[i].comment,
        };
        this.movieInternalItems.push(newItem);
      });
    },
  },
};
</script>