<template>
    <div>
        <h1> Shopping Cart Details</h1>
        <CartItemCard v-for="item in product" :key="item.id" :product="product"/>
        <CartSummaryPayment :product="product"/>
    </div>
</template>

<script>
import CartItemCard from '../components/cart/CartItemCard.vue'
import CartSummaryPayment from '../components/cart/CartSummaryPayment.vue'

export default {
    components:{
        CartItemCard,
        CartSummaryPayment
    },
    computed: {
        product() {
            return this.$store.getters.cartItems
        }
    }   
}
</script>

<style lang="scss">
</style>