<template lang="html">
  <div>
    <h1>Posts</h1>
    <div v-for="post in postList" class="container">
      <b-card>
        <b-media>
          <div class="row">
            <div class="col-4">
              <img :src="post.img_url" style="max-height: 300px; max-width: 250px" alt="">
            </div>
            <div class="col-8">
              <h3>{{post.title}} by {{post.author}}</h3>
              <p>{{post.content}}</p>
              <p>Votes: {{post.votes}}</p>
            </div>
          </div>
        </b-media>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Posts',
  props: {
    posts: {
      type: Array
    }
  },
  data () {
    return {
      postList: this.posts
    }
  }
}
</script>
