<script>
import { store } from "../store.js";
import AppCard from './AppCard.vue'
export default {
  name: 'AppMain',
  components:{
    AppCard,
  },
  data() {
    return {
      store,
    };
  },
}
</script>

<template>
  <div class="section-main">
    <h2 v-if="(store.movies.length > 0)">FILM</h2>
    <AppCard :details="movie" v-for="movie in store.movies" />
    <h2 v-if="(store.series.length > 0)">SERIE TV</h2>
    <AppCard :details="serie" v-for="serie in store.series" />
  </div>
</template>

<style lang="scss" scoped>
@use '../style/partials/variables' as *;

.section-main{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;

  h2{
    color: $primary-color;
    text-align: center;
    font-size: 32px;
    width: 100%;
    margin-top: 20px;
    border: 3px solid $primary-color;
    background-color: $secondary-color;
  }
}
</style>