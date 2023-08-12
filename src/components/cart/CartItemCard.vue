<template>
    <div class="cart-item-card">
        <div class="header">
            <h3> {{ item_name }}</h3>
            <h4>Item in Cart: {{ item_qty }}</h4>
            <h4>Total Cost: {{ item_price }}</h4>
        </div>
        <p> {{ item_description }}</p>
    </div>
</template>

<script>

export default {
    props: ['product'],
    computed: {
        item_description(){
            return this.product.map(i => i.description).toString()
        },
        item_qty() {
            return this.product.map(i => i.quantity).toString()
        },
        item_name() {
            return this.product.map(i => i.name).toString()
        },
        item_price() {
            return this.$store.getters.cartTotal
        }
    }
}
</script>

<style lang="scss">
    .cart-item-card {
        width: 90%;
        margin: 5%;
        background-color: white;
        box-shadow: 0 0 5px gray;
        border-radius: 5px;
        padding: 10px;
        text-align: left;
        
        .header {
            display: flex;
            justify-content: space-around;
        }
    }
</style>