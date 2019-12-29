<template>
    <div>
        <h1>shopping cart</h1>
        <ul>
            <li v-for="product in products" :key="product.id">
                {{product.title}} -- {{product.price | currency}} -- {{product.quantity}}
            </li>
        </ul>
        <p>Total: {{total | currency}}</p>
        <button @click="$store.dispatch('checkout')">Checkout</button>
        <p>{{$store.state.checkoutStatus}}</p>
    </div>
</template>

<script>
    export default {
      computed: {
        products() {
          return this.$store.getters.cartProducts
        },

        total() {
          return this.$store.getters.cartTotal
        }
      }
    }
</script>