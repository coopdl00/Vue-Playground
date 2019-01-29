<template lang="html">
  <div>
    <h1 class="col-12">Books</h1>
    <div v-for="book in books" class="container">
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
import axios from 'axios'
export default {
  name: 'Books',
  data () {
    return {
      books: null
    }
  },
  mounted () {
    axios.get('https://collective-api-coopdl00.herokuapp.com/api/books').then(response => (this.books = response.data))
  }
}
</script>
