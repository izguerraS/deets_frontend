<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <!-- <h1>{{ recipes }}</h1> -->
    <div v-for="recipe in recipes">
      <h3><a v-bind:href="`/recipes/${recipe.id}`">{{ recipe.title }}</a></h3>
      <p>{{ recipe.directions }}</p>
      <hr>
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
      message: "Welcome to the index page!",
      recipes: []
    };
  },
  created: function() {
    this.indexRecipes();
  },
  methods: {
    indexRecipes: function() {
      console.log('in recipes index');
      axios.get('/api/recipes').then(response => {
        console.log(response.data);
        this.recipes = response.data;
      })
    }
  }
};
</script>