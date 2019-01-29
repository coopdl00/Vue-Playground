<template lang="html">
  <div>
    <h1>Shopping-Cart</h1>
    <div v-for="product in productList" class="container">
      <b-card>
        <b-media>
          {{product.name}}
          {{formatValues(product.priceInCents)}}
        </b-media>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShoppingCart',
  props: {
    products: {
      type: Array
    }
  },
  methods: {
    formatValues (number) {
      let arr = number.toString().split("")
      return arr.map((element, index) => {
        if (index === 0) {
          return `$${element}`
        } else if (index === arr.length - 2) {
          return `.${element}`
        } else {
          return element
        }
      }).join("")
    }
  },
  data () {
    return {
      productList: this.products
    }
  }
}
</script>
