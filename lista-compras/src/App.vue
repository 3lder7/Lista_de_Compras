<template>
  <div id="app">
    <h1>Lista de Compras</h1>
    <AddItemForm @item-added="addItemToList" />
    <ShoppingList
      :items="shoppingList.map((item, index) => ({
        ...item,
        index,
      })).filter(item => !item.bought)"
      @item-bought="markItemAsBought"
    />
  </div>
</template>


<script>
import AddItemForm from "./components/AddItemForm.vue";
import ShoppingList from "./components/ShoppingList.vue";

export default {
  name: "App",
  components: {
    AddItemForm,
    ShoppingList,
  },
  data() {
    return {
      shoppingList: [], // Armazena os itens da lista
    };
  },
  methods: {
    addItemToList(item) {
      this.shoppingList.push({ name: item, bought: false });
      console.log("Lista de Compras Atualizada:", this.shoppingList); // Log para depuração
    },
    markItemAsBought(index) {
      this.shoppingList[index].bought = true; // Marca como comprado
      console.log("Item marcado como comprado:", this.shoppingList[index]);
   },
  },
};
</script>
