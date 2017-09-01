<template>
<table class="table">
    <thead>
        <tr>
            <th>Name</th>
            <th>Description</th>
            <th>Price</th>
        </tr>
    </thead>
    <tbody>
        <tr v-for="product in products" track-by="id">
            <td>{{product.name}}</td>
            <td>{{product.description}}</td>
            <td>{{product.price}}</td>
        </tr>
    </tbody>
</table>
</template>
<script>
export default {
  data () {
      return {
          products: [
              {
                  id:'2342424242423',
                  name: 'cobol 101 vintage',
                  description: 'Learn cobol with this vintage programming book',
                  price: 399
              },
              {
                  id:'23423442asf342',
                  name: 'Sharp c2719 curved tv',
                  description: 'Watch TV like never before with the brand new curved screen technology',
                  price: 1995
              },
              {
                  id:'34545309034343',
                  name: 'Remmington X mechanical keyboard',
                  description: 'Excellent for gaming and typing, this Remmington X keyboard features tactile, clicky switches for speed and accuracy',
                  price: 595
              }

          ]
      }

  }
}
</script>
<style scoped>

.header {
    font-size: 4rem;
}
</style>


