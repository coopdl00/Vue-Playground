<template>
<div>
  <NavBar/>
  <div class="container">
    <div class="row">
      <b-button-toolbar class="mx-lg-auto">
        <b-button-group class="mx-1">
          <b-btn v-on:click="toggleBook()">Books</b-btn>
          <b-btn v-on:click="toggleCamera()">Cameras</b-btn>
          <b-btn v-on:click="toggleComment()">Comments</b-btn>
          <b-btn v-on:click="toggleMessage()">Messages</b-btn>
          <b-btn v-on:click="toggleMovie()">Movies</b-btn>
          <b-btn v-on:click="togglePost()">Posts</b-btn>
          <b-btn v-on:click="toggleProduct()">Shopping Cart</b-btn>
          <b-btn v-on:click="toggleUser()">Users</b-btn>
        </b-button-group>
      </b-button-toolbar>
    </div>
  </div>
  <div class="container">
    <div v-if="this.book" class="row">
      <h1 class="col-12">Books</h1>
      <div v-for="book in books" class="container">
        <b-card>
          <b-media>
            <h5 class="mt-0">{{ book.subject }}</h5>
            <p>{{ book.body }}</p>
          </b-media>
          {{ book }}
        </b-card>
      </div>
    </div>
    <div v-if="this.camera" class="row">
      <h1>Cameras</h1>
      <div v-for="camera in cameras" class="container">
        <b-card>
          <b-media>
            <div class="row">
              <div class="col-3">
                <img :src="camera.picture" style="max-width: 300px; max-height: 250px" alt="">
              </div>
              <div class="col-9">
                <div class="row">
                  <h5 class="col-3 mt-0">{{ camera.name }}</h5>
                  <p class="col-3">Rating: {{ camera.rating }}/5 Stars</p>
                  <p class="col-3">Price: ${{ camera.price }}</p>
                </div>
                <div class="row">
                  <div v-if="camera.onSale">
                    <img style="max-width: 100px; max-height: 100px" src="https://www.covingtonscustoms.com/Pics/Parts/Installed/PartsGroups/OnSale.jpg" alt="">
                  </div>
                </div>
              </div>
            </div>
          </b-media>
        </b-card>
      </div>
    </div>
    <div v-if="this.comment" class="row">
      <h1>Comments</h1>
      <div v-for="comment in comments" class="container">

      </div>
    </div>
    <div v-if="this.message" class="row">
      <h1>Messages</h1>
    </div>
    <div v-if="this.movie" class="row">
      <h1>Movies</h1>
    </div>
    <div v-if="this.post"class="row">
      <h1>Posts</h1>
    </div>
    <div v-if="this.product" class="row">
      <h1>Shopping-Cart</h1>
    </div>
    <div v-if="this.user" class="row">
      <h1>Users</h1>
    </div>
  </div>
</div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import axios from 'axios'

export default {
  components: {
    NavBar
  },
  methods: {
    toggleBook () {
      if (this.book) {
        this.book = false
      } else {
        this.book = true
      }
    },
    toggleCamera () {
      if (this.camera) {
        this.camera = false
      } else {
        this.camera = true
      }
    },
    toggleComment () {
      if (this.comment) {
        this.comment = false
      } else {
        this.comment = true
      }
    },
    toggleMessage () {
      if (this.message) {
        this.message = false
      } else {
        this.message = true
      }
    },
    toggleMovie () {
      if (this.movie) {
        this.movie = false
      } else {
        this.movie = true
      }
    },
    togglePost () {
      if (this.post) {
        this.post = false
      } else {
        this.post = true
      }
    },
    toggleProduct () {
      if (this.product) {
        this.product = false
      } else {
        this.product = true
      }
    },
    toggleUser () {
      if (this.user) {
        this.user = false
      } else {
        this.user = true
      }
    },
  },
  data () {
    return {
      books: null,
      book: false,
      cameras: null,
      camera: false,
      comments: null,
      comment: false,
      messages: null,
      message: false,
      movies: null,
      movie: false,
      posts: null,
      post: false,
      products: null,
      product: false,
      users: null,
      user: false
    }
  },
  mounted () {
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/messages').then(response => (this.books = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/cameras').then(response => (this.cameras = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/comments').then(response => (this.comments = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/messages').then(response => (this.messages = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/movies').then(response => (this.movies = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/posts').then(response => (this.posts = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/products').then(response => (this.products = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/users').then(response => (this.users = response.data))
  }
}
</script>
