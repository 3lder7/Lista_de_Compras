<template>
  <form @submit.prevent="addItem">
    <input
      type="text"
      v-model="newItem"
      placeholder="Digite o item"
      required
    />
    <button type="submit">Adicionar</button>
  </form>
</template>

<script>
export default {
  name: "AddItemForm",
  data() {
    return {
      newItem: "", // Armazena o nome do item digitado
    };
  },
  methods: {
    addItem() {
      if (this.newItem.trim() === "") return;

      // Emite o item para o componente pai
      this.$emit("item-added", this.newItem.trim());
      this.newItem = ""; // Limpa o campo
    },
  },
};
</script>

<style>
form {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 8px 16px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #369c73;
}
</style>
