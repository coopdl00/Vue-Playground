<template lang="html">
  <div>
    <h1 class="col-12">Cameras</h1>
    <div v-for="camera in cameraList" class="container">
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
</template>

<script>
import axios from 'axios'
export default {
  name: 'Cameras',
  props: {
    cameras: {
      type: Array
    }
  },
  data () {
    return {
      cameraList: this.cameras
    }
  }
}
</script>
