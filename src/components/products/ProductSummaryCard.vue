<template>
    <div class="card">
        <h3> {{ product.name }} </h3>
        <h5 class="price"> Price: ${{ product.price.toFixed(2) }} </h5>
        <p class="description"> Description: {{ product.description }}</p>
        <p class="text"> {{  product.category }}</p>
        <button class="view-product-button" @click="$emit('view-product', product)"> View </button>
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
    background-color: white;
    box-shadow: 0 0 5px gray;
 
    h5.price {
    color: gray;
    }

    p.description {
        font-size: .85rem;
    }

    p.text {
        color: gray;
    }
}

button.view-product-button {
        padding: 1rem;
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