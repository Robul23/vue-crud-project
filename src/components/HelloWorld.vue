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
          <v-toolbar-title>Movietify</v-toolbar-title>
          <v-divider class="mx-4" inset vertical> </v-divider>
          <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Caută"
            single-line
            clearable
            class="shrink"
            hide-details=""
          ></v-text-field>
          <v-divider class="mx-4" inset vertical> </v-divider>
        </v-toolbar>
      </template>
      <template v-slot:[`item.actions`]="{ item }">
                <v-btn
                  v-on:click="edit(item)"
                  color="#1F51FF"
                  dark
                  fab
                  x-small
                  elevation="2"
                >
                  <v-icon>edit</v-icon>
                </v-btn>

                <v-btn
                  v-on:click="delet(item)"
                  color="#FF3131"
                  fab
                  dark
                  x-small
                  elevation="2"
                >
                  <v-icon>delete_forever</v-icon>
                </v-btn>
              </template>
    </v-data-table>
    </template>
  </v-container>
</template>

<script>
import "material-design-icons-iconfont/dist/material-design-icons.css";
export default {
  name: "HelloWorld",
  icons: {
    iconfont: "mdi",
  },

  data: () => ({
    search:"",
    headers: [
      {
        text: "Title",
        sortable: true,
        value: "title",
      },
      { text: "Type", value: "type" },
      { text: "Year", value: "year" },
      { text: "Watched", value: "watched" },
      { text: "Actions", value: "actions", sortable: false },
    ],
    movies: [
      {
        title: "Mario",
        type: "Tv Show",
        year: 2019,
        watched: true,
      },
      {
        title: "Morbius",
        type: "Movie",
        year: 2022,
        watched: false,
      },
    ],
  }),

  methods: {
    edit(item) {
      console.log("a fost editat" + item)
      
    },
    delet(item) {
      console.log("a fost sters" + item)
      
    }

  }
};
</script>
