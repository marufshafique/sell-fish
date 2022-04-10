<script setup>
import { ref, unref } from "vue";

const form = ref({
  type: null,
  size: null,
  count: null,
  price: null,
});

const emit = defineEmits(["create"]);

function onSubmit() {
  emit("create", JSON.parse(JSON.stringify(form.value)));

  form.value.type = null;
  form.value.size = null;
  form.value.count = null;
  form.value.price = null;
}
</script>

<template>
  <div>
    <form @submit.prevent="onSubmit">
      <label for="type">Type</label>
      <select v-model="form.type" name="type" id="type">
        <option value="sea">Sea fish</option>
        <option value="river">River fish</option>
        <option value="pond">Pond fish</option>
      </select>

      <label for="size">Size</label>
      <select v-model="form.size" name="size" id="size">
        <option value="s">S</option>
        <option value="m">M</option>
        <option value="l">L</option>
      </select>

      <label for="count">Count</label>
      <input v-model="form.count" type="number" id="count" />

      <label for="price">Price</label>
      <input v-model="form.price" type="number" id="price" />

      <button type="submit">Create</button>
    </form>
  </div>
</template>
