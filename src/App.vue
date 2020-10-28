<template>
  <div id="app">
  <!-- Navigation -->
  <nav class="navbar navbar-expand-lg navbar-light fixed-top" id="mainNav">
    <div class="container">
      <a class="navbar-brand" href="">The Cookbook</a>
      <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
        Menu
        <i class="fas fa-bars"></i>
      </button>
      <div class="collapse navbar-collapse" id="navbarResponsive">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <button class="navbar-brand" href="/signup" v-if="!isLoggedIn()" ><router-link to="/signup">Signup</router-link></button>
          </li>
          <br>
          <li class="nav-item">
            <button class="navbar-brand" href="/login" v-if="!isLoggedIn()" ><router-link to="/login">Log-in</router-link></button>
          </li>
          <li class="nav-item">
            <button class="navbar-brand" href="/recipes" v-if="isLoggedIn()" ><router-link v-if="isLoggedIn()" to="/recipes">All Recipes</router-link></button>
          </li>
          <br>
          <li class="nav-item">
            <button class="navbar-brand" href="/recipes/new" v-if="isLoggedIn()" ><router-link v-if="isLoggedIn()" to="/recipes/new">New Recipe</router-link></button>
          </li> 
           <hr>
          <li class="nav-item">
            <button class="navbar-brand" href="/logout" v-if="isLoggedIn()" ><router-link v-if="isLoggedIn()" to="/logout">Logout</router-link></button>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Page Header -->
  <!-- <header class="masthead" style="background-image: url('/img/Mexican_food.jpg')">
    <div class="overlay"></div>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div class="site-heading">
            <h1>The Cookbook</h1>
            <span class="subheading">
               Digital Cookbook to Share Our Family's Favorite Recipes. </span>
          </div>
        </div>
      </div>
    </div>
  </header> -->


  <router-view/>
  <hr>

  <!-- Footer -->
  <footer>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <ul class="list-inline text-center">
            <li class="list-inline-item">
              <a href="https://twitter.com/IzguerraS">
                <span class="fa-stack fa-lg">
                  <i class="fas fa-circle fa-stack-2x"></i>
                  <i class="fab fa-twitter fa-stack-1x fa-inverse"></i>
                </span>
              </a>
            </li>
            <li class="list-inline-item">
              <a href="https://dev.to/izguerras">
                <span class="fa-stack fa-lg">
                  <i class="fas fa-circle fa-stack-2x"></i>
                  <i class="fab fa-dev fa-stack-1x fa-inverse"></i>
                </span>
              </a>
            </li>
            <li class="list-inline-item">
              <a href="https://github.com/izguerraS">
                <span class="fa-stack fa-lg">
                  <i class="fas fa-circle fa-stack-2x"></i>
                  <i class="fab fa-github fa-stack-1x fa-inverse"></i>
                </span>
              </a>
            </li>
          </ul>
          <p class="copyright text-muted">Copyright &copy; Your Website 2020</p>
        </div>
      </div>
    </div>
  </footer>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #cc7e35;
}
</style>

<script>
export default {
  methods: {
    isLoggedIn: function() {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function() {
      return localStorage.getItem("user_id");
    }
  }
}
</script> 