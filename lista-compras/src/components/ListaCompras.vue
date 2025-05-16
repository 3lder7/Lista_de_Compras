<template>
  <ul>
    <li
      v-for="(item, originalIndex) in items" :key="originalIndex"
    >
      <span>{{ item.name }}</span>
      <button @click="markAsBought(item.index)">Concluir</button>
    </li>
  </ul>
</template>
  
<script>
export default {
  name: "ShoppingList",
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    markAsBought(index) {
      this.$emit("item-bought", index);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 8px;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 4px 8px;
  cursor: pointer;
}

button:hover {
  background-color: #369c73;
}
</style>
