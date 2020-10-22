<template>
  <div class="recipes-new">
      <header class="masthead" style="background-image: url('/img/Mexican_food.jpg')">
    <div class="overlay"></div>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div class="site-heading">
            <h1>New Recipe</h1>
            <span class="subheading">
               Share Your Latest/Greatest Dish! </span>
          </div>
        </div>
      </div>
    </div>
  </header>
    <form v-on:submit.prevent="submit()">
      <h1>Make a new recipe</h1>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Title:</label> 
        <input type="text" class="form-control" placeholder="Title" required data-validation-required-message="Please enter a title." v-model="title">
      </div>
      <div class="form-group">
        <label>Ingredients:</label> 
        <textarea rows="5" class="form-control" placeholder="Ingredients" required data-validation-required-message="Please enter ingredients." v-model="ingredients"></textarea>
      </div>
      <div class="form-group">
        <label>Directions:</label>
        <textarea rows="5" class="form-control" placeholder="Directions" required data-validation-required-message="Please enter directions." v-model="directions"></textarea>
      </div>
      <div class="form-group">
        <label>Prep Time:</label>
        <input type="text" class="form-control" placeholder="Prep Time" required data-validation-required-message="Please enter a prep time." v-model="prepTime">
      </div>
      <div class="form-group">
        <label>Image Url:</label>
        <input type="text" class="form-control" placeholder="example: http://www.recipes.com/image" required data-validation-required-message="Please enter an image." v-model="imageUrl">
      </div>
      <input type="submit" class="btn btn-primary" value="Submit">
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      title: "",
      ingredients: "",
      directions: "",
      prepTime: "",
      imageUrl: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        title: this.title,
        ingredients: this.ingredients,
        directions: this.directions,
        prep_time: this.prepTime,
        image_url: this.imageUrl,
      };
      console.log(params);
      
      axios
        .post("/api/recipes", params)
        .then(response => {
          this.$router.push("/recipes");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
      
    }
  }
};
</script>