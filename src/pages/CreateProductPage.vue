<template>
    <div class="container my-5">
        <h1>Create Product</h1>

        <form @submit.prevent="createProduct">
            <div class="mb-3">
                <label for="name" class="form-label">Product Name</label>
                <input type="text" v-model="product.name" class="form-control" id="name">
            </div>

            <div class="mb-3">
                <label for="price" class="form-label">Price</label>
                <input type="number" v-model="product.price" class="form-control" id="price">
            </div>

            <div class="mb-3">
                <label for="stock" class="form-label">Stock</label>
                <input type="number" v-model="product.stock" class="form-control" id="stock">
            </div>

            <button type="submit" class="btn btn-primary">Submit</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            product: {
                name: '',
                stock: 0,
                price: 0
            }
        }
    },

    methods: {
        async createProduct() {
            const res = axios.post('http://localhost:3000/api/products', this.product);
            
            this.$router.push({ path: '/' })
        }
    },
}
</script>

<style lang="scss" scoped></style>