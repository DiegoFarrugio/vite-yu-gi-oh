<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
  data(){
    return{
        store,
        baseUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
    }
  },

  methods: {

    getAllarchetype(){
            axios.get(this.store.archetypeUrl).then((response) => {
                console.log("Archetype:",response);
                this.store.archetypes = response.data;
                console.log("Archetype",this.store.archetypes);
         });
        }

  },

  created(){
    axios.get(this.store.baseUrl).then((response) => {
      console.log(response.data.data);
      this.store.characters = response.data.data;
      console.log(this.store.characters);
    });

    this.getAllarchetype()

  },

  

  components: {
    AppHeader,
    AppMain,
    AppFooter
  }
}

</script>



<template>
  <AppHeader/>
  <AppMain/>
  <AppFooter/>
</template>



<style lang="scss">
@use "./assets/scss/main.scss" as *;
</style>
