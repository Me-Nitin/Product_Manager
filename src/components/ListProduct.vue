<template>
   <b-col md="4" class="m-3">
    <b-card header="List Product">
      
      <b-card-group deck> 
      <b-card
        :border-variant="product.inventoryStatus ? 'success':'danger' "
        align="center"
        v-for="product in products" :key="product.id"
       class="my-3">
        <b-badge class="mb-2" :style=" { backgroundColor: product.inventoryStatus?  'green': 'red' }"> {{product.inventoryStatus? 'IN STOCK':'OUT OF STOCK'}} </b-badge>       
        <b-card-text><strong>Name: </strong> {{product.name}}</b-card-text>
        <b-card-text><strong>Price: </strong> {{product.price}}</b-card-text>
        <b-card-text><strong>Brand: </strong> {{product.brand}}</b-card-text>
        <hr>
        <b-row>
          <b-col>
            <b-button variant="danger" @click="deleteProduct(product.id)"><i class="fa-solid fa-trash"></i></b-button>
          </b-col>
          <b-col>
           <UpdateProduct  :product="product"  @updateProduct="updateProduct"/>
          </b-col>
        </b-row>
      </b-card>
      </b-card-group>  
    </b-card>
  </b-col> 
</template>

<script>

import UpdateProduct from './UpdateProduct.vue'
export default {
props : ['products'],
components: {
 UpdateProduct
},
methods: {
  deleteProduct(productId){
    this.$emit('deleteProduct',productId);
  },
  updateProduct(updatedProduct){
this.$emit('updateProduct', updatedProduct);
  }
}
}
</script>

<style >

</style>
