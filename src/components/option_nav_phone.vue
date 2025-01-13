<template>
  <div style="width: 100%; min-height: 200px; background-color:#545E9B" class="main p-2 gap-2 fol jen">
    <div class="force-center">

      <div class="fow gap-2 ">
        <img class="" width=24 src="assets/search.svg" alt="">
        <input style="border: none; outline: none" class=" w-100 rounded-3 p-1" type="text" placeholder="Search...">
      </div>
    </div>
    <div class="my-1"></div>
    <p class="f-12 text-light fw-bold">
      Genre
    </p>
    <div class="fol gap-1 ">

      <div class="fol option-container gap-1">
        <a href="#" class="text-decoration-none">Shooter</a>
      </div>
      <div class="fol option-container">
        <a href="#" class="text-decoration-none">Shooter</a>
      </div>
      <div class="fol option-container">
        <a href="#" class="text-decoration-none">Shooter</a>
      </div>
    </div>
  </div>
</template>
<!-- -->

<script setup>
</script>
<!-- -->

<style scoped>
  .main{
  border-radius: 8px;
  opacity: 0;
  display: none;
  transition: all 500ms ease;
  }
  .option-container a{
  padding: 4px;
  color: white;
  border-bottom: 1px solid black;
  border-radius: 2px;
  background-color: #545E9B;
  }
  .option-container a:active{
  opacity: 0.5
  }
</style>