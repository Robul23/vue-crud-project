<template>
  <v-app>
    <div class="see">
      <h1>Movie data view</h1>
      <v-form class="formSee">
        <v-text-field
          v-model="formEdit.idMovie"
          label="ID"
          type="number"
          readonly
          outlined
        ></v-text-field>

        <v-text-field
          v-model="formEdit.title"
          label="Title"
          readonly
          outlined
        ></v-text-field>

        <v-select
          v-model="formEdit.movieType"
          :items="types"
          label="Type"
          readonly
          outlined
        ></v-select>

        <v-select
          v-model="formEdit.genre"
          :items="genres"
          label="Genre"
          readonly
          outlined
        ></v-select>

        <v-text-field
          v-model="formEdit.year"
          label="Year"
          readonly
          outlined
        ></v-text-field>

        <v-textarea
          v-model="formEdit.description"
          label="Description"
          readonly
          outlined
        ></v-textarea>

        <v-checkbox
          v-model="formEdit.watched"
          label="Watched"
          readonly
          outlined
        ></v-checkbox>
        <v-btn class="mr-4" @click="back()"> Go back </v-btn>
      </v-form>
    </div>
  </v-app>
</template>

<script>
export default {
  name: "SeeView",
  props: ["items"],
  data: () => ({
    types: ["Movie", "Tv show", "Cartoon"],
    genres: [
      "Action",
      "Comedy",
      "Drama",
      "Fantasy",
      "Horror",
      "Mystery",
      "Romance",
      "Thriller",
    ],
    formEdit: {
      idMovie: null,
      year: "",
      description: "",
      movieType: "",
      genre: "",
      title: "",
      watched: false,
    },
  }),

  created() {
    this.fetch();
  },

  methods: {
    fetch() {
      this.formEdit.idMovie = this.items.idMovie;
      this.formEdit.year = this.items.year;
      this.formEdit.description = this.items.description;
      this.formEdit.movieType = this.items.movieType;
      this.formEdit.genre = this.items.genre;
      this.formEdit.title = this.items.title;
      this.formEdit.watched = this.items.watched;
    },

    back() {
      this.$router.push({ path: "/" });
    },
  },
};
</script>

<style></style>
