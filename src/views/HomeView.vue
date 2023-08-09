<template>
  <div class="home">
    <Drawer 
    :product="product"
    :active="active.product_drawer"    
    />
    <div class="product-card-container">
      <ProductSummaryCard v-for="product in items" :key="product.id" :product="product"
      v-on:view-product="viewProduct($event)"/>
    </div>
  </div>
</template>

<script>
import items from '../mochdata/item.js'
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue'
import Drawer from '../components/products/ProductDescription.vue'

export default {
  name: 'HomeView',
  components: {
    ProductSummaryCard,
    Drawer
  },
  data() {
    return {
      product: null,
      items: items,
      active: {
        product_drawer: false
      }
    }
  },
  methods:{
    viewProduct(product) {
      this.product = product
    }
  }
}
</script>

<style lang="scss">

.product-card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
