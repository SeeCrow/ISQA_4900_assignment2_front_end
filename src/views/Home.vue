<template>
  <!-- <h1> Welcome to the Movie Page</h1> -->
  <!-- <h3 class="topQuote"> "Every great film should seem new everytime you see it" Robert Ebert </h3> -->


  <div class="container-fluid">
    <div class="row">
      <div class="col">
        <blockquote class="fs-5">
          Welcome {{ validUserName }}!
          <footer>
            <small>
              <em
                >&mdash; Every great film should seem new every time you see it.
                - Roger Ebert</em
              >
            </small>
          </footer>
        </blockquote>
      </div>
    </div>
  </div>


  <div class="container-fluid">
    <div class="row align-items-center justify-content-center" >
      <div class="col-12 col-sm-10 col-md-8">
        <div class="card">
          <div class="row g-0">
            <div class="col-md-6">
              <div class="card-body">
                <h5 class="card-title">Movies</h5>
                <p class="card-text">
                  Click below to get descriptions and ratings of movies you
                  are interested in watching.
                </p>
                  <a @click="viewMovies" class="btn btn-primary">View Details</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>


</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import router from "../router";


export default {
  name: "Home",
  components: {},
  data: () => ({
    validUserName: "Guest",
  }),
  mounted() {
    this.getUser();
  },
  methods: {
    viewMovies() {
      router.push("/movie-list");
    },
    getUser() {
      if (
        localStorage.getItem("isAuthenticates") &&
        JSON.parse(localStorage.getItem("isAuthenticates")) === true
      ) {
        this.validUserName = JSON.parse(localStorage.getItem("log_user"));
      }
    },
  },
};
</script>

<style>
h3 {
  font-style: italic;
}
</style>