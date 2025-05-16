<template>
  <ul>
    <li v-for="(item, index) in items" :key="index" class="bought-item">
      <span>{{ item.name }}</span>
      <button @click="removeItem(index)">Excluir</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "BoughtItems",
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    removeItem(index) {
      this.$emit("item-removed", index);
    },
  },
};
</script>

<style scoped>
.bought-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 8px;
  color: #aaa;
  text-decoration: line-through;
}

button {
  background-color: #e74c3c;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 4px 8px;
  cursor: pointer;
}

button:hover {
  background-color: #c0392b;
}
</style>