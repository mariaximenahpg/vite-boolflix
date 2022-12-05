<script>
import { store } from "../store.js";
export default {
  name: 'AppHeader',
  data() {
    return {
      store,
    };
  },
}
</script>

<template>
  <header>
    <img src="../assets/boolflixLogo.png" alt="">
    <form @submit.prevent="$emit('search')" action="">
      <input v-model="store.searchText" type="text" placeholder="Cerca film, serie TV...">
      <button type="submit">Cerca</button>
    </form>
  </header>
</template>

<style lang="scss" scoped>
@use '../style/partials/variables' as *;

header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 50px;
  img{
    margin-left: 40px;
  }
  input{
    border: none;
    border-radius: 5px;
    padding: 12px 180px 12px 10px;
    margin-right: 20px;   
  }
  button{
    color: $primary-color; 
    background-color: $secondary-color; 
    cursor: pointer;
    border: 2px solid $primary-color;
    border-radius: 5px;
    padding: 10px;
    margin-right: 40px;  
  }
}
</style>