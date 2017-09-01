<template>
<section>
    <save-prodct-form 
    :product="productInForm" v-on:submit="onFormSave"
    >
    </save-prodct-form>
    <product-list></product-list>
</section>
  
</template>
<script>
import ProductList from './ProductList'
import SaveProductForm from './SaveProductForm'
export default {
  
}
</script>

