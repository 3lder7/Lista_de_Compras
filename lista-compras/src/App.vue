<template>
  <div id="app">
    <h1>Lista de Compras</h1>
    <AddItemForm @item-added="addItemToList" />
    <h2>Itens Pendentes</h2>
    <ShoppingList
      :items="shoppingList.map((item, index) => ({
        ...item,
        index,
      })).filter(item => !item.bought)"
      @item-bought="markItemAsBought"
    />
    <h2>Itens Já Comprados</h2>
    <BoughtItems
      :items="shoppingList.filter(item => item.bought)"
      @item-removed="removeBoughtItem"
    />
  </div>
</template>

<script>
import AddItemForm from "./components/AddItemForm.vue";
import ShoppingList from "./components/ShoppingList.vue";
import BoughtItems from "./components/BoughtItems.vue";

export default {
  name: "App",
  components: {
    AddItemForm,
    ShoppingList,
    BoughtItems,
  },
  data() {
    return {
      shoppingList: [], // Lista de compras com estado
    };
  },
  methods: {
    addItemToList(item) {
      this.shoppingList.push({ name: item, bought: false });
    },
    markItemAsBought(index) {
      this.shoppingList[index].bought = true; // Atualiza o estado do item
    },
    removeBoughtItem(index) {
      this.shoppingList.splice(index, 1); // Remove o item da lista
    },
  },
};
</script>

<style>
h1, h2 {
  color: #ffffff;
}

#app {
  font-family: Arial, sans-serif;
  padding: 20px;
}
</style>