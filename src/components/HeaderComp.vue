<template>
  <div class="d-flex justify-content-between align-items-center">
    <i class="fa-brands fa-spotify"></i>
    <select name="" id="">
      <option value="">seleziona il genere</option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'HeaderComp'
}
</script>

<style lang="scss" scoped>
div {
  height: 60px;
  padding: 0 15px;
  background-color: #2E3A46;
}

i {
  color: #58BF59;
  font-size: 2rem;
}

select {
  height: fit-content;
  border: none;
  font-size: .85rem;
  padding: 7px 10px;
  border-radius: 3px;
}

</style>