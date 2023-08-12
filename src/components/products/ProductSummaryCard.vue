<template>
    <div class="card">
        <h3 class="product-name"> {{ product.name }} </h3>
        <h5 class="price"> Price: ${{ product.price.toFixed(2) }} </h5>
        <p class="description"> Description: {{ product.description }}</p>
        <p class="text"> {{  product.category }}</p>
        <button class="view-product-button" @click="$emit('view-product', product)"> View Detail </button>
    </div>
</template>

<script>
export default {
    props: ['product'],
    computed: {
        description() {
            return this.product.description.substring(0, 150)
        }
    }
}
</script>

<style lang="scss">
 .card {
    width: 80%;
    margin: 10%;
    padding: 1rem;
    border-radius: 0.5rem;
    background-color: black;
    box-shadow: 0 0 5px gray;
 
    h5.price {
      color: skyblue;
    }

    .product-name {
        color: skyblue;
    }

    p.description {
        font-size: .85rem;
        color: white;
    }

    p.text {
        color: white;
        font-weight: bolder;
        text-transform: uppercase;
    }
}

button.view-product-button {
        padding: 0.8rem;
        background-color: rgb(76, 160, 187);
        border: none;
        color: white;
        font-weight: bold;
        font-size: 1rem;
        border-radius: 5px;
        cursor: pointer;
    }

@media (min-width: 500px) {
    .card {
        width: 350px;
        margin: 10px;
    }
}

</style>