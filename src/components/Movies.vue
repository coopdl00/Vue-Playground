<template lang="html">
  <div>
    <h1>Movies</h1>
    <div v-for="movie in movieList" class="container">
      <b-card>
        <b-media>
          <div class="row">
            <div class="col-4">
              <img :src="movie.Poster" alt="">
            </div>
            <div class="col-8">
              <h3>{{movie.Title}}</h3>
              <h6> written by {{movie.Writer}} rated {{movie.Rated}}, Released in {{movie.Released}} with a runtime of {{movie.Runtime}}</h6>
              <p>Actors: {{movie.Actors}}</p>
              <p>{{movie.Plot}}</p>
              <ul v-for="critic in movie.Ratings">
                <li>{{critic.Source}} rated {{critic.Value}}</li>
              </ul>
              <p>Website: {{movie.Website}}</p>
            </div>
          </div>
        </b-media>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Movies',
  props: {
    movies: {
      type: Array
    }
  },
  data () {
    return { movieList: this.movies }
  }
}
</script>
