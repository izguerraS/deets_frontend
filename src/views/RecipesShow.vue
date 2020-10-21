
<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h1>title: {{ recipe.user_id }}</h1>
    <h1>ingredients: {{ recipe.ingredients }}</h1>
    <h1>prep_time: {{ recipe.prep_time }}</h1>

    <img v-bind:src="recipe.image_url">

    <p>recipe.user_id {{recipe.user_id}}</p>
    <p>current user's id {{ $parent.getUserId() }}</p>
    
    <div v-if="recipe.user_id == $parent.getUserId()">

      <a v-bind:href="`/recipes/${recipe.id}/edit`">Edit this item</a>




    <p><button v-on:click="deleteRecipe()">Delete the recipe</button></p>




    </div>

  </div>
</template>
<style>
</style>
<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Welcome to The show page!",
      recipe: {}
    };
  },
  created: function() {
    this.showRecipe();
  },
  methods: {
    showRecipe: function() {
      console.log('showing the recipe...');
      console.log(this.$route);
      // params[:id]      
      axios.get(`/api/recipes/${this.$route.params.id}`).then(response => {
        console.log(response.data);
        this.recipe = response.data;
      })
    },
    deleteRecipe: function() {
      console.log('deleting the recipe...');
      axios.delete(`/api/recipes/${this.$route.params.id}`).then(response => {
        console.log(response.data);
        this.$router.push('/recipes')
      })
    }
  }
};
</script>