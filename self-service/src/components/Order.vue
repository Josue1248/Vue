<template>
    <section class="summary">
        <strong>Order Details</strong>
        <table>
            <thead>
                <tr>
                    <th>Item</th>
                    <th>Total</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(product, n) in products" :key="n">
                    <td>{{product.quantity}}x {{product.name}}</td>
                    <td>{{product.quantity * product.price}}</td>
                </tr>
                <tr>
                    <th>Total</th>
                    <th>{{this.total}}</th>
                </tr>
            </tbody>
        </table>
    </section>
</template>

<script>
export default {
    data(){
        return {
            total: 0
        }
    },
    props: ['products'],
    methods: {
        getTeamDetails(){
            
        }
    },
    watch: {
        products:  function(){
            if(this.products.length > 0){
                this.products.forEach(product => {
                    this.total += product.quantity * product.price
                });
            } else {
                this.total = 0
            }

        }
    }
}
</script>

<style>
</style>