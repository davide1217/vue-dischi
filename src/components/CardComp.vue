<template>
  <div class="_col col-2 d-flex flex-column align-items-center">
    <img :src="album.poster" alt="">
    <h6>{{album.title}}</h6>
    <span>{{album.author}}</span>
    <span>{{album.year}}</span>
  </div>
</template>

<script>
export default {
  name: 'CardComp',
  props: {
    album: Object,
  }
}
</script>

<style lang="scss" scoped>

  img {
    width: 100%;
  }

  h6 {
    color: white;
    text-transform: uppercase;
    margin-top: 20px;
    font-size: .8rem;
  }

  span {
    color: #85807D;
    text-align: center;
  }

  span:last-child {
    font-size: .8rem;
  }
</style>