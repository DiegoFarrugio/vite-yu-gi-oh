<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';


export default {
  data(){
    return{
        baseUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
        characters: [],
    }
  },

  methods: {},

  created(){
    axios.get(this.baseUrl).then((response) => {
      console.log(response.data.data);
      this.characters = response.data.data;
      console.log(this.characters);
    });
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
  <AppMain :allCharacters="characters"/>
  <AppFooter/>
</template>



<style lang="scss">
@use "./assets/scss/main.scss" as *;
</style>
