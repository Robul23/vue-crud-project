<template>
  <v-app>
    <div class="edit">
      <h1>Movie form</h1>
      <v-form 
      class="formEdit">

        <v-text-field
         v-model="formEdit.idMovie"
          label="ID" 
          type="number"
          disabled
          v-show="false"
          ></v-text-field>

        <v-text-field
         v-model="formEdit.title"
          label="Title" 
          ></v-text-field>
         

        <v-select
          v-model="formEdit.movieType"
          :items="types"
          label="Type"
        ></v-select>

         <v-select
          v-model="formEdit.genre"
          :items="genres"
          label="Genre"
        ></v-select>

        <v-text-field
         v-model="formEdit.year"
          label="Year" 
          ></v-text-field>

        <v-textarea
          v-model="formEdit.description"
          label="Description"
        ></v-textarea>

         <v-checkbox
      v-model="formEdit.watched"
      label="Watched"
    ></v-checkbox>
     <v-btn
      class="mr-4"
      @click="edit()"
    >
      Edit
    </v-btn>
    <v-btn @click="cancel()">
      Cancel
    </v-btn>
      </v-form>
      <br>
      <p>{{formEdit}}</p>
      <br>
    </div>
  </v-app>
</template>

<script>
import axios from "axios";


export default {
  name: "EditView",
  props: ['items'],
  data: () => ({
    types: ["Movie", "Tv show", "Cartoon"],
    genres:['Action', 'Comedy','Drama','Fantasy','Horror','Mystery','Romance','Thriller'],
    formEdit: {
    idMovie: null,
    year: "",
    description: "",
    movieType: "",
    genre:"",
    title: "",
    watched: false,
    }
    
  }),

    created() {
      this.fetch();
  },


  methods: {

    fetch() {
      this.formEdit.idMovie = this.items.idMovie
      this.formEdit.year = this.items.year
      this.formEdit.description = this.items.description
      this.formEdit.movieType = this.items.movieType
      this.formEdit.genre = this.items.genre
      this.formEdit.title = this.items.title
      this.formEdit.watched = this.items.watched
            
    },


    cancel() {
      this.$router.push({ path: '/' })
    },
    edit() {
      axios.put('https://localhost:44394/api/movies/' + this.formEdit.idMovie, this.formEdit, )
        .then((response) => response.data);
         console.log(this.formEdit.data)
        this.$router.push({ path: '/' })

     
    },


  },
};
</script>

<style>

</style>
