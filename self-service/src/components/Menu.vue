<template>
    <section class="items">
        <h4>Pick your items</h4>
        <div v-for="(product, n) in products" :key="n" :class="product.active ? 'product selected' : 'product'" @click="selectProduct(product)">
            <div class="photo">
                <img :src="product.photo">
            </div>
            <div class="description">
                <span class="name">{{product.name}}</span>
                <span class="price">{{product.price}}</span>
                <div :hidden="!product.active" class="quantity-area">
                    <button :disabled="product.quantity <= 1" @click.stop="product.quantity--">-</button>
                    <span class="quantity">{{product.quantity}}</span>
                    <button @click.stop="product.quantity++">+</button>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: ['products'],
    methods:{
        selectProduct: function(item){
            item.active = !item.active;
            this.$emit('productChange', item);
        }
    }
}
</script>

<style>

</style>