<template>
  <main>

    <HeaderComp :albumsGenre="albumsGenre" :albumsAuthors="albumsAuthors"
     @filterGenre="filterGenre" @filterAuthor="filterAuthor"/>

    <div class="_container">
      <div v-if="isLoaded" class="container-fluid">

        <div v-if="activeGenre == '' " class="row flex-wrap">
          <CardComp 
          v-for="(album, index) in albums" :key="`album-${index}}`"
          :album="album"/>
        </div>

        <div v-else class="row flex-wrap">

          <CardComp 
           v-for="(album, index) in albumsFiltered" :key="`album-${index}}`"
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
import HeaderComp from './HeaderComp.vue';

export default {
  components: { CardComp, GifComp, HeaderComp },
  name: 'MainComp',
    
  data() {
    return {
      
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',

      albums: [],

      albumsGenre: [],

      albumsAuthors: [],

      isLoaded: false,

      activeGenre: 'All',

      activeAuthor: 'All',
    }
  },

  mounted() {
    this.getApi();
  },

  methods: {
    filterGenre(genre) {
      this.activeGenre = genre;
    },

    filterAuthor(author) {
      this.activeAuthor = author;
    },

    getApi() {
      axios.get(this.apiUrl)
        .then(file => {
          this.albums = file.data.response;
          this.isLoaded = true;
          this.getAlbumsGenre();
          this.getAlbumsAuthors();
        })
    },

    getAlbumsGenre() {

      for (const album of this.albums) {
        
        if (!this.albumsGenre.includes(album.genre)) {
          this.albumsGenre.push(album.genre)
        }
      }
    },

    getAlbumsAuthors() {

      for (const album of this.albums) {
  
        if (!this.albumsAuthors.includes(album.author)) {
          this.albumsAuthors.push(album.author)
        }
      }
    },

    albumsFilter(album) {
      
      if(this.activeGenre != 'All' && this.activeAuthor != 'All') {
        return album.genre == this.activeGenre && album.author == this.activeAuthor
      }
       else if(this.activeGenre != 'All' || this.activeAuthor != 'All') {
        return album.genre == this.activeGenre || album.author == this.activeAuthor
      }
       else {
        return album == album
      }
    }

  },

  computed: {

    albumsFiltered() {

      return  this.albums.filter(this.albumsFilter)

    }
  }
}
</script>

<style lang="scss" scoped>
  main {
    min-height: 100vh;
    background-color: #1E2D3B;
    padding-bottom: 50px;

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