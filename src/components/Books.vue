<template lang="html">
  <div>
    <h1 class="col-12">Books</h1>
    <div v-for="book in bookList" class="container">
      <b-card>
        <b-media>
          <h4>{{book.title}} by {{book.author}}</h4>
          <h6>{{book.subtitle}}</h6>
          <p>Summary: ({{book.pages}} pages) Price: ${{book.price}}</p>
          <p>{{book.description}}</p>
          <p>Published by : {{book.publisher}}<br> Website Link: <a>{{book.website}}</a></p>
        </b-media>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Books',
  props: {
    books: {
      type: Array
    }
  },
  data () {
    return {
      bookList: this.books
    }
  }
}
</script>
