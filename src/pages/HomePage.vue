<template>
    <div class="container my-5">
        <h1>Product List</h1>

        <RouterLink class="btn btn-primary my-3" to="/create">Add Product</RouterLink>

        <table class="table">
            <thead>
                <tr>
                    <th scope="col">Product Name</th>
                    <th scope="col">Price</th>
                    <th scope="col">Stock</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(data, index) of products" :key="'index-product-' + index">
                    <td>{{ data.name }}</td>
                    <td>{{ formatRupiah(data.price) }}</td>
                    <td>{{ data.stock }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from 'axios';
import { RouterLink } from 'vue-router';

export default {
    data() {
        return {
            products: []
        }
    },

    mounted() {
        this.getProduct();
    },

    methods: {
        async getProduct() {
            const res = await axios.get("http://localhost:3000/api/products");
            this.products = res.data.data;
        },

        formatRupiah(number) {
            return new Intl.NumberFormat("id-ID", {
            style: "currency",
            currency: "IDR"
            }).format(number);
        }
    }
}
</script>

<style lang="scss" scoped></style>