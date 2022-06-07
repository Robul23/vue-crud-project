<template>
  <v-app>
    <div class="form">
      <h1>Movie form</h1>
      <v-form 
      class="form">

        <v-text-field
         v-model="form.title"
          label="Title" 
          ></v-text-field>

        <v-select
          v-model="form.movieType"
          :items="types"
          label="Type"
        ></v-select>

         <v-select
          v-model="form.genre"
          :items="genres"
          label="Genre"
        ></v-select>

        <v-text-field
         v-model="form.year"
          label="Year" 
          ></v-text-field>

        <v-textarea
          v-model="form.description"
          label="Description"
        ></v-textarea>

         <v-checkbox
      v-model="form.watched"
      label="Watched"
    ></v-checkbox>
     <v-btn
      class="mr-4"
      @click="submit"
    >
      submit
    </v-btn>
    <v-btn @click="clear">
      clear
    </v-btn>
      </v-form>
      <br>
      <p>{{form}}</p>
      <br>
    </div>
  </v-app>
</template>

<script>
import axios from "axios";


export default {
  data: () => ({
    types: ["Movie", "Tv show", "Cartoon"],
    genres:['Action', 'Comedy','Drama','Fantasy','Horror','Mystery','Romance','Thriller'],
    form: {
    title: "",
    movieType: null,
    genre:null,
    year:null,
    description:"",
    watched: false,
    }
    
  }),

  methods: {

    clear() {
      this.form.title = "";
      this.form.movieType = null;
      this.form.genre = null;
      this.form.year = null;
      this.form.description = "";
      this.form.watched = false
    },
    submit() {
        axios.post('https://localhost:44394/api/movies', this.form)
          .then((response) => response.data,
          this.$router.push({ path: '/' }));

     
    },


  },
};
</script>

<style>

</style>
