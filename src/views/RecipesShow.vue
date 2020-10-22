
<template>
  <div class="home">
      <header class="masthead" style="background-image: url('/img/Mexican_food.jpg')">
    <div class="overlay"></div>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div class="site-heading">
            <h1>{{ recipe.title }}</h1>
            <span class="subheading">
               Created by: {{ recipe.chef}} </span>
          </div>
        </div>
      </div>
    </div>
  </header>


  <div class="container">
    <div class="row">
      <div class="col-lg-8 col-md-10 mx-auto">
       <p> <h4>Ingredients:</h4> {{ recipe.ingredients }} </p>
       <p> <h4>Prep Time:</h4> {{ recipe.prep_time }} </p>
         <p> <h4>Directions:</h4> {{ recipe.directions }} </p>
         <!-- <h4>Image:</h4> {{ recipe.image_url }} -->

         <p><img v-bind:src="recipe.image_url"></p>

    <div v-if="recipe.user_id == $parent.getUserId()">
      <a v-bind:href="`/recipes/${recipe.id}/edit`">Edit this item</a>
    <p><button v-on:click="deleteRecipe()">Delete the recipe</button></p> </div>

      </div>
    </div>
  </div>


    <!-- <h1>{{ message }}</h1>
    <h1>title: {{ recipe.user_id }}</h1>
    <h1>ingredients: {{ recipe.ingredients }}</h1>
    <h1>prep_time: {{ recipe.prep_time }}</h1>

    <img v-bind:src="recipe.image_url"> -->

    <!-- <p>recipe.user_id {{recipe.user_id}}</p>
    <p>current user's id {{ $parent.getUserId() }}</p> --> 





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