<template>
   <b-col md="4" class="m-3">
    <b-card header="List Product">
      
      <b-card-group deck> 
      <b-card
        :border-variant="product.inventoryStatus ? 'success':'danger' "
        align="center"
        v-for="product in products" :key="product.id"
       class="my-3">
        <b-badge class="mb-2" :style=" { backgroundColor: product.inventoryStatus?  'green': 'red' }">{{product.inventoryStatus ? 'IN STOCK':'OUT OF STOCK'}}</b-badge>       
        <b-card-text><strong>Name: </strong> {{product.name}}</b-card-text>
        <b-card-text><strong>Price: </strong> {{product.price}}</b-card-text>
        <b-card-text><strong>Brand: </strong> {{product.brand}}</b-card-text>
      </b-card>

      </b-card-group>  
    </b-card>
  </b-col> 
</template>

<script>
export default {
props : ['products']
}
</script>

<style >

</style>
