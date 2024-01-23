<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
  data(){
    return{
      searchText : '',
      searchStatus : '',
      store,
    }
  },

  methods: {

    archetypeSearch(){
            if(store.selectUser.length > 0){
                console.log("hai cliccato");
                this.store.urlSearchArchetype = 'https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=';
                store.urlSearchArchetype = store.urlSearchArchetype + store.selectUser
                console.log("url", store.urlSearchArchetype);
                store.baseUrl = store.urlSearchArchetype
                
                axios.get(this.store.baseUrl).then((response) => {
                console.log(response.data.data);
                this.store.characters = response.data.data; 
                console.log("CARDS",this.store.characters);
                this.store.loaded = true; 
         });
            }
        }
  
  }
}
</script>



<template>
  <header>
    <div class="big-container">
    <div class="row">
      <div class="col">
        <h2 class="p-2">
          Yu-Gi-Oh Api
        </h2>
      </div>
    </div>

    <div>
      <select v-model="store.selectUser" class="form-select" aria-label="Status">
        <option selected>Select</option>
        <option v-for="(archetype, i) in store.archetypes" :value="archetype.archetype_name">{{ archetype.archetype_name }}</option>
      </select>

      
      <button @click="archetypeSearch()" type="button" class="btn btn-primary mt-3">
        Search
      </button>

      
  </div>

  </div>
  </header>
</template>



<style lang="scss" scoped>
@use "../assets/scss/header.scss" as *;
</style>
