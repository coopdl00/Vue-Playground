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
      <Books/>
    </div>
    <div v-if="this.camera" class="row">
      <Cameras/>
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
import Books from './components/Books.vue'
import Cameras from './components/Cameras.vue'
import axios from 'axios'

export default {
  components: {
    NavBar,
    Books,
    Cameras
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
      book: false,
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
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/comments').then(response => (this.comments = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/messages').then(response => (this.messages = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/movies').then(response => (this.movies = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/posts').then(response => (this.posts = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/products').then(response => (this.products = response.data))
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/users').then(response => (this.users = response.data))
  }
}
</script>
