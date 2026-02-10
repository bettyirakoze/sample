<template>
  <div class="container">
    <h2>Live Product Search</h2>

    <input
      type="text"
      v-model="search"
      placeholder="Search products..."
      class="search-input"
    />
    <ul v-if="filteredProducts.length" ref="dropdown">
      <li v-for="product in filteredProducts" :key="product.id">
        {{ product.name }}
      </li>
    </ul>

    <p v-else>No results found</p>
  </div>
</template>

<script setup>
import { ref, computed, onUpdated } from "vue";

const search = ref("");
const dropdown = ref(null);

const products = ref([
  { id: 1, name: "Laptop" },
  { id: 2, name: "Phone" },
  { id: 3, name: "Headphones" },
  { id: 4, name: "Keyboard" },
  { id: 5, name: "Mouse" },
  { id: 6, name: "Monitor" },
]);
const filteredProducts = computed(() => {
  return products.value.filter((p) =>
    p.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
onUpdated(() => {
  console.log("Filtered results:", filteredProducts.value);

  if (dropdown.value) {
    console.log("Dropdown height:", dropdown.value.offsetHeight + "px");
  }
});
</script>
<style>
.container {
  max-width: 300px;
  margin: 40px auto;
  font-family: Arial;
}
.search-input {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
}
ul {
  border: 1px solid #9a3232;
  padding: 3;
  list-style: none;
}

li {
  padding: 8px;
  border-bottom: 1px solid #06174c;
}
</style>
kwjdocdavpfl