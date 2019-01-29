<template>
<div>
  <NavBar/>
  <div class="container">
    <div class="row">
      <b-button-toolbar class="mx-lg-auto">
        <b-button-group class="mx-1">
          <b-btn v-on:click="toggle('book')">Books</b-btn>
          <b-btn v-on:click="toggle('camera')">Cameras</b-btn>
          <b-btn v-on:click="toggle('comment')">Comments</b-btn>
          <b-btn v-on:click="toggle('message')">Messages</b-btn>
          <b-btn v-on:click="toggle('movie')">Movies</b-btn>
          <b-btn v-on:click="toggle('post')">Posts</b-btn>
          <b-btn v-on:click="toggle('product')">Shopping Cart</b-btn>
          <b-btn v-on:click="toggle('user')">Users</b-btn>
        </b-button-group>
      </b-button-toolbar>
    </div>
  </div>
  <div class="container">
    <div v-if="this.book" class="row">
      <Books :books="this.books"/>
    </div>
    <div v-if="this.camera" class="row">
      <Cameras :cameras="this.cameras"/>
    </div>
    <div v-if="this.comment" class="row">
      <Comments :comments="this.comments"/>
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
import Comments from './components/Comments.vue'
import axios from 'axios'

export default {
  components: {
    NavBar,
    Books,
    Cameras,
    Comments
  },
  methods: {
    toggle (e) {
      if (this[e]) {
        this[e] = false
      } else {
        this[e] = true
      }
    }
  },
  data () {
    return {
      book: false,
      camera: false,
      comment: false,
      message: false,
      movie: false,
      post: false,
      product: false,
      user: false,
    }
  },
  mounted () {
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/books').then(response => (this.books = response.data))
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
