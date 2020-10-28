<template>
  <div class="home">
      <header class="masthead" style="background-image: url('/img/full_table.jpg')">
    <div class="overlay"></div>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div class="site-heading">
            <h1>All Recipes</h1>
            <span class="subheading">
               The Collection of Family Recipes </span>
          </div>
        </div>
      </div>
    </div>
  </header>
    <div class="container">
    <div class="row">
      <div class="col-lg-8 col-md-10 mx-auto">
        <div v-for="recipe in recipes" class="post-preview">
          <a v-bind:href="`/recipes/${recipe.id}`">
            <h2 class="post-title">
              {{ recipe.title }}
            </h2>
            <h3 class="post-subtitle">
              {{  recipe.directions }}
            </h3>
          </a>
          <p class="post-meta">Posted by
            <a href="#">{{ recipe.chef }}</a>
            on {{ recipe.created_at }}</p>      
          <hr>
        </div>
      
        <!-- Pager -->
        <!-- <div class="clearfix">
          <a class="btn btn-primary float-right" href="#">Older Posts &rarr;</a>
        </div> -->
      </div>
    </div>
  </div>  
    <!-- <h1>{{ message }}</h1>

    <input type="text" v-model="searchTerm" list="titles">

    <datalist id="titles">
      <option v-for="recipe in recipes">{{ recipe.title }}</option>
    </datalist>     -->

      <!-- <div v-for="recipe in orderBy(recipes, 'directions')">

      <h3><a v-bind:href="`/recipes/${recipe.id}`">{{ recipe.title }}</a></h3>
      <p>{{ recipe.directions | uppercase }}</p>
      <hr>
    </div> -->
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
import Vue2Filters from 'vue2-filters'

export default {
  data: function() {
    return {
      message: "Welcome to the index page!",
      recipes: [],
      searchTerm: "",
      msg: "hello"
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
  },
  mixins: [Vue2Filters.mixin],
};
</script>