<template lang="html">
  <div>
    <h1>Comments</h1>
    <div v-for="comment in commentList" class="container">
      <b-card>
        <b-media>
          Post number {{comment.post_id}} {{comment.content}}
        </b-media>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Comments',
  props: {
    comments: {
      type: Array
    }
  },
  data () {
    return {
      commentList: this.comments
    }
  }
}
</script>
