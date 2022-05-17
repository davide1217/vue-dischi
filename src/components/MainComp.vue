<template>
  <main>
    <div class="_container">
      <div v-if="isLoaded" class="container-fluid">
        <div class="row flex-wrap">

          <CardComp v-for="(album, index) in albums" :key="`album-${index}}`"
           :album="album"/>

        </div>

      </div>

      <GifComp v-else />

    </div>
  </main>
</template>

<script>
import CardComp from './CardComp.vue';
import axios from 'axios';
import GifComp from './GifComp.vue';

export default {
  components: { CardComp, GifComp },
  name: 'MainComp',

  data() {
    return {
      
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',

      albums: [],

      isLoaded: false,
    }
  },

  mounted() {
    this.getApi();
  },

  methods: {
    getApi() {
      axios.get(this.apiUrl)
        .then(file => {
          this.albums = file.data.response;
          this.isLoaded = true;
        })
    }
  }
}
</script>

<style lang="scss" scoped>
  main {
    min-height: calc(100vh - 60px);
    background-color: #1E2D3B;
    padding: 50px 0;

    ._container {
      width: 70%;
      height: 100%;
      margin: auto;

      ._col {
        background-color: #2E3A46;
        margin: 0 15px 30px;
        padding: 12px 12px 50px;
      }

    }
  }
</style>