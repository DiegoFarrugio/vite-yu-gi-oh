<script>
export default {
  data(){
    return{

    }
  },

  props: {
    allCharacters: Array
  },

  methods: {}
}
</script>



<template>

  <main>
    <div class="big-container background-container">
    <select class="p-2 ms-4 mt-3" name="" id="">Scegli
      <option value="">Alien</option>
    </select>

    <div class="row mt-3">
      <div class="col-12 col-sm-6 col-md-3 mt-4 p-2 text-center " v-for="(character, i) in allCharacters" :key="i">
        <div class="single-character">
          <div>
            <img class="w-75" :src="character.card_images[0].image_url" alt="">
          </div>
          <div>
            <h3 class="mb-3 fs-5 text-white">
              {{ character.name }}
            </h3>
            <h4 class="fs-4">
              {{ character.frameType }}
            </h4>
          </div>
        </div>

      </div>

    </div>
  </div>
  </main>

</template>



<style lang="scss" scoped>

</style>
