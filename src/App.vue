<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';


export default {
  data(){
    return{

    }
  },

  methods: {},

  mounted(){
    axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0').then((response) => {
      console.log(response);
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
  <AppMain/>
  <AppFooter/>
</template>



<style lang="scss">
@use "./assets/scss/main.scss" as *;
</style>
