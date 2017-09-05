<template>
<section>
    <div class="panel panel-default">
        <div class="panel-body">
            <save-product-form 
            :product="productInForm" v-on:submit="onFormSave" v-on:cancel="onCancelClicked"
            >
            </save-product-form>
            <div class="panel panel-default">
                <div class="panel-heading">
                    <strong>Product List</strong>
                </div>
                <div class="panel-body">
                    <product-list :products='products' v-on:edit="onEditClicked" v-on:remove="onRemoveClicked"></product-list>
                </div>
            </div>
        </div>
    </div>
</section>
</template>
<script>
import ProductList from './ProductList'
import SaveProductForm from './SaveProductForm'
import uuidv4 from 'uuid/v4'
const initialData = () => {
    return {
        productInForm: {
            id: null,
            name: '',
            description: '',
            price: null
        },

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
export default {
    components: {
        ProductList,
        SaveProductForm
    },
    data: initialData,
    methods: {
        onFormSave(product){
            const index = this.products.findIndex((p)=>p.id === product.id)
            if (index!==-1){
                this.products.splice(index, 1, product)
            }else {
                product.id=uuidv4()
                this.products.push(product)
            }
            this.resetProductInForm()
        },
        resetProductInForm () {
            this.productInForm = initialData().productInForm;
        },
        onEditClicked (product){
            console.log("cick edit");
            this.productInForm = {...product}
        },
        onCancelClicked () {
            console.log("click cancel")
            this.resetProductInForm()
        },
        onRemoveClicked (productId) {
            console.log("click remove")
            const index = this.products.findIndex((p)=> p.id === productId)
            this.products.splice(index,1)
            if (productId === this.productInForm.id){
                this.resetProductInForm()
            }
        }

    }
  
}
</script>

