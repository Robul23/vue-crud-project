<template>
  <v-app>
    <div class="edit">
      <h1>Movie edit</h1>
      <v-form class="form">

        <v-text-field
         v-model="form.title"
          label="Title" 
          ></v-text-field>

        <v-select
          v-model="form.type"
          :items="types"
          label="Type"
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
      @click="edit"
    >
      edit
    </v-btn>
    <v-btn @click="cancel">
      Cancel
    </v-btn>
      </v-form>
      <br>
      <p>{{form}}</p>
    </div>
  </v-app>
</template>

<script>
import axios from "axios";


export default {
  data: () => ({
    types: ["Movie", "Tv show", 'Cartoon'],
    form: {
    title: "",
    type: null,
    year:null,
    description:"",
    watched: false,
    }
    
  }),

  methods: {

    cancel() {
      this.$router.push({ path: '/' })
    },
    edit() {
        axios.post('https://form-vue-d82a6-default-rtdb.firebaseio.com', this.form)
        .then((response) => response.data);
        console.log(this.form)

     
    },


  },
};
</script>

<style>

</style>
