<template>
  <option_nav_phone ref='shit' ></option_nav_phone>
  <div class="d-lg-none fow alen text-light">
    <div style="flex-basis:0;  flex-grow: 1" class="">
      
    </div>
    <div style="flex-basis:0;  flex-grow: 1" class="">
      <div class="fow alen jen gap-1 ">

        <img width="45" src="assets/el_logo.svg" alt="">
        <div class="f-24 fw-bold">
          FreeGame
        </div>
      </div>
    </div>
    <div id="ham"style="flex-basis:0; flex-grow: 1" class=" fow justify-content-end">
      <img :onclick="open_nav" width="45" src="assets/el_burger_menu.svg" alt="">

    </div>


  </div>

</template>
<!-- -->

<script setup>
  
  import {useTemplateRef} from 'vue'
  import option_nav_phone from './option_nav_phone.vue'
  
  const r_option= useTemplateRef('shit')
  function open_nav(){
  r_option.value.$el.classList.toggle('show')
  }
  
</script>
<!-- -->

<style scoped>
  #ham:active{
    opacity:0.5
  }
  .show{
  opacity: 1!important;
  display: flex
}
</style>