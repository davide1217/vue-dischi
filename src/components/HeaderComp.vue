<template>
  <header class="d-flex justify-content-between align-items-center">
    <i class="fa-brands fa-spotify"></i>

    <div>
      <select @change="$emit('filterGenre', selectValue)" v-model="selectValue" name="" id="">
        <option value="All">tutti i generi</option>

        <option v-for="genre in albumsGenre" 
        :value="genre"
        :key="genre"
        >{{genre}}</option>

      </select>

      <select @change="$emit('filterAuthor', selectAuthor)" v-model="selectAuthor" name="" id="">
        <option value="All">tutti gli autori</option>

        <option v-for="author in albumsAuthors" 
        :value="author"
        :key="author"
        >{{author}}</option>

      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  props: {
    albumsGenre: Array,
    albumsAuthors: Array,
  },
  data() {
    return {
      selectValue: 'All',
      selectAuthor: 'All',
    }
  }
}

</script>

<style lang="scss" scoped>
header {
  height: 60px;
  padding: 0 15px;
  margin-bottom: 50px;
  background-color: #2E3A46;
}

i {
  color: #58BF59;
  font-size: 2rem;
}

select {
  margin: 0 10px;
  height: fit-content;
  border: none;
  font-size: .85rem;
  padding: 7px 10px;
  border-radius: 3px;
}

</style>