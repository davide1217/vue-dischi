<template>
  <div id="loading">
    <span>
      <span>boolean</span><br>
      is workin for you
    </span>
  </div>
</template>

<script>
export default {
  name: 'GifComp'
}
</script>

<style lang='scss' scoped>

#loading {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 25%;
  height: 45%;
  border-top: 6px solid #66DB64;
  border-bottom: 6px solid #011432;
  border-left: 6px solid #1E2D3B;
  border-right: 6px solid #1E2D3B;
  border-radius: 50%;
  color: white;
  text-align: center;
  padding-top: 10%;
  font-size: 1.5rem;

  & > span {
    position: absolute;
    left: 26%;
    top: 40%;
  }

  span > span {
    text-transform: uppercase;
  }

}

body:hover #loading {
    animation: rotating 2s ease infinite;
  }

  @keyframes rotating {

    25% {
      transform: rotate(90deg);
      left: 37.5%;
      top: 27.5%;
    }
    50% {
      transform: rotate(180deg);
      left: 37.5%;
      top: 27.5%;
    }
    75% {
      transform: rotate(270deg);
      left: 37.5%;
      top: 27.5%;
    }
    100% {
      transform: rotate(360deg);
      left: 37.5%;
      top: 27.5%;
    }
  }

  body:hover #loading > span {
    animation: Rotating 2s ease infinite;
  }

  @keyframes Rotating {
    25% {
      transform: rotate(-90deg);
    }
    50% {
      transform: rotate(-180deg);
    }
    75% {
      transform: rotate(-270deg);
    }
    100% {
      transform: rotate(-360deg);
    }
  }
</style>