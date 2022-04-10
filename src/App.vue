<script setup>
import { ref } from "vue";

import AddStockForm from "./components/AddStockForm.vue";

const stockList = ref([]);
function addItemToList(item) {
  stockList.value = [...stockList.value, item];
}

const cartList = ref([]);
function addToCart(item) {
  cartList.value = [...cartList.value, item];
}

const showCart = ref(false);
function onViewCart() {
  showCart.value = true;
}
</script>

<template>
  <AddStockForm @create="addItemToList" />

  <hr />

  <button @click="onViewCart">View Cart</button>

  <div v-if="showCart">
    <h1>Your items</h1>
    <ul>
      <li v-for="(fish, index) in cartList" :key="index">
        type: {{ fish.type }} size: {{ fish.size }} count:
        {{ fish.count }} price:
        {{ fish.price }}
      </li>
    </ul>
  </div>

  <ul v-else>
    <li v-for="(fish, index) in stockList" :key="index">
      type: {{ fish.type }} size: {{ fish.size }} count: {{ fish.count }} price:
      {{ fish.price }}

      <button @click="addToCart(fish)">Add to cart</button>
    </li>
  </ul>
</template>
