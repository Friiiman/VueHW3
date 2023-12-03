<template>
    <div class="catalog">
        <h1 class="catalog__title">Catalog</h1>
        <div class="catalog__products">
            <div v-for="product in products" :key="product.id" class="product-card">
                <h3 class="product-card__name">{{ product.name }}</h3>
                <p class="product-card__price">{{ formattedPrice(product.price) }}</p>
                <p class="product-card__available" v-if="product.available">Available</p>
                <p class="product-card__available product-card__available--not" v-else>Out of stock</p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'ProductDetails',

    data() {
        return {
            products: [
                {
                    name: 'Product 1',
                    price: '99.99',
                    available: true
                },
                {
                    name: 'Product 2',
                    price: '199.99',
                    available: true
                },
                {
                    name: 'Product 3',
                    price: '10000',
                    available: false
                },
                {
                    name: 'Product 4',
                    price: '50',
                    available: true
                }
            ]
        };
    },

    computed: {
        formattedPrice() {
            return price => `$ ${price}`
        }
    }
};
</script>

<style>
.catalog__title {
    margin-bottom: 50px;
}

.catalog__products {
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 50px;
}

.product-card {
    padding: 25px;
    border: 1px solid #000;
}

.product-card__available {
    font-style: italic;
    color: green;
}

.product-card__available--not {
    color: red;
}
</style>
