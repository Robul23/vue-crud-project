<template>
  <v-container>
    <template>
      <v-data-table
        :headers="headers"
        :items="movies"
        class="elevation-1"
        :search="search"
      >
        <template v-slot:top>
          <v-toolbar flat>
            <v-toolbar-title>Movie data table</v-toolbar-title>
         
            <v-spacer></v-spacer>
          </v-toolbar>
        </template>
        <template v-slot:[`item.actions`]="{ item }">
          <v-btn v-on:click="goToEdit(item)" color="#1F51FF" dark fab x-small>
            <v-icon>edit</v-icon>
          </v-btn>

          <v-btn v-on:click="delet(item)" color="#FF3131" fab dark x-small>
            <v-icon>delete_forever</v-icon>
          </v-btn>

          <v-btn v-on:click="view(item)" color="#FFFF00" fab dark x-small>
            <v-icon>visibility</v-icon>
          </v-btn>
        </template>
      </v-data-table>
    </template>
  </v-container>
</template>

<script>
import axios from "axios";
import "material-design-icons-iconfont/dist/material-design-icons.css";
export default {
  name: "DataTable",
  icons: {
    iconfont: "mdi",
  },

  data: () => ({
    search: "",
    headers: [
      {
        text: "Title",
        sortable: true,
        value: "title",
      },
      { text: "ID", value: "idMovie" },
      { text: "Type", value: "movieType" },
      { text: "Genre", value: "genre" },
      { text: "Year", value: "year" },
      { text: "Watched", value: "watched" },
      { text: "Actions", value: "actions", sortable: false },
    ],
    movies: [],
  }),

  mounted() {
    this.fillTable();
  },

  created() {
    this.fillTable();
  },

  methods: {
    async fillTable() {
      axios.get("https://localhost:44394/api/movies").then((response) => {
        this.movies = response.data;
      });
    },
    goToEdit(item) {
      console.log(item.idMovie);
      this.$router.push({
        name: "edit",
        params: {
          items: item,
        },
      });
    },
    delet(item) {
      axios
        .delete("https://localhost:44394/api/movies/" + item.idMovie)
        .then((response) => {
          this.movies = response.data.data;
          this.fillTable();
        });

      console.log("a fost sters" + item.idMovie);
    },

    view(item) {
      console.log(item)
       this.$router.push({
        name: "see",
        params: {
          items: item,
        },
      });
    }
  },
};
</script>
