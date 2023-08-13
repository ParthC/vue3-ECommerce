<template>
    <div class="drawer-background" :class="{ show: active }" @click="$emit('close-drawer')"></div>
    <div class="drawer" :class="{show: active}">
        <div class="drawer-close" @click="$emit('close-drawer')">
            X
        </div>
        <div v-if="product" class="product-details">
            <h3 class="text-center"> {{ product.name  }}</h3>
            <p class="description"> {{ product.description  }}</p>
            <h3 class="text-center"> ${{ product.price.toFixed(2) }}</h3>

            <div class="cart-total" v-if="product_total">
                <h3>Total</h3>
                <h4> {{ product_total }}</h4>
            </div>

            <div class="button-container">
                <button class="add" @click="addToCart()"> Add To Cart </button> 
                <button class="remove" @click="removeFromCart()"> Remove </button> 
            </div>
        </div>  
    </div>
</template>

<script>
export default {
    props: ['product', 'active'],
    emits: ["close-drawer"],
    methods: {
        addToCart() {
            this.$store.commit('addToCart', this.product)
        },
        removeFromCart() {
            this.$store.commit('removeFromCart', this.product)
        }
    },
    computed: {
        product_total() {
            return this.$store.getters.productQauntity(this.product);
        }
    }
}
</script>

<style lang="scss">

.drawer-background {
    width: 100%;
    height: 100vh;
    position: fixed;
    left: 0;
    top: 0;
    background-color: rgba(137, 152, 170, 0.5);
    z-index: 100;
    display: none;
    transition: display .5s;
    &.show{
        display: block;
    }
}

.drawer {
    width: 95vw;
    height: 100vh;
    background-color: skyblue;
    position: fixed;
    top: 0;
    left: -105vw;
    padding: 1.5rem;
    transition: left .5s;
    z-index: 101;
    overflow-y: scroll;
    

    &.show{
        left: 0;
    }
}

.drawer-close {
    font-size: 1.5rem;
    padding: 5px;
    border-radius: 5px;
    right: 10px;
    border: 2px;
    border: 2px solid gray;
    color: gray;
    width: 15px;
    float: right;
    cursor: pointer;

    &:hover{
        background-color: rgb(212, 114, 114);
    }
}


.product-details {
    display: flex;
    justify-content: center;
    flex-direction: column;

    p.description {
        padding: 20px;
        line-height: 1.5rem;
    }

    .button-container {
        button {
            width: 150px;
            border: none;
            padding: 10px;
            border-radius: 5px;
            margin: 0 5px 50px 5px;
            cursor: pointer;
            color: white;
            background-color: black;
        }
    }
}

@media (min-width: 500px) {
    .drawer {
        width: 450px;
    }
}   
</style>