<script>
import {store} from "./store.js";
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
  created(){
    axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php").then((response)=>{
      this.store.carte= response.data.data;
      this.store.n = response.data.data.length;
      console.log(this.store.carte);
    });
  }
}
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style>
body {
  background-color: #d48f38;
}
</style>
