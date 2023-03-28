<script>
import { store } from "./store.js";
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  name: "app",
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      store
    }
  },
  methods: {
    crea() {
      axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php").then((response) => {
        this.store.carte = response.data.data.slice(0, 50); //inserisco al massimo 50 elementi nell'array
        console.log(this.store.carte);
      });
    },
    search() {
      if (this.store.cerca !== '') {
        axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=" + this.store.cerca).then((response) => {
          this.store.carte = response.data.data;
          console.log(this.store.carte);
        });
      }
      else this.crea();
    }
  },
  created() {
    this.crea();
  }
}
</script>

<template>
  <AppHeader />
  <AppMain @cerca="search" />
</template>

<style>
body {
  background-color: #d48f38;
}
</style>
