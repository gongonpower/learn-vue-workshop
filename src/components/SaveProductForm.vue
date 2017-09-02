<template>
<form action="">
    <div class="form-group">
      <label for="productName">Product Name</label>
      <input type="text" v-model="product.name" placeholder="input your name" maxlength="30" class="form-control" id="productName">
    </div>
    <div class="form-group">
      <label for="productDescription">Product Description</label>
      <textarea type="text" v-model="product.description" placeholder="input your description" rows="3" class="form-control" id="productDescription"></textarea>
    </div>
    <div class="form-group">
      <label for="price">Price</label>
      <input type="number" v-model="product.price" placeholder="input price"  class="form-control" id="price">
    </div>
    <button class="btn btn-primary" type="submit" v-on:click.prevent="onSubmit">Save product</button>
    <button class="btn btn-alert" type="button" v-if='product.id !==null' v-on:click.prevent="onCancel">Cancel</button>
</form>

</template>
<script>
export default {
  props: ['product'],
  methods: {
      onSubmit () {
          this.$emit('submit', this.product)
      },
      onCancel () {
        console.log('emit cancel')
        this.$emit('cancel')
      }
  }
}
</script>

