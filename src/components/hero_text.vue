<template>
  
  <div style="width: 300px; min-width: 300px" class="fol pore">
    <div class="element z-0">
      <img ref='block' class="posa" width="140" style='bottom:-40px; left: -30px; transition: all 1s ease' fill=black src="assets/el_dots.svg" alt="">
      <img style="top:-70px" class="posa top_left" width="80" src="assets/el_dbl_block.svg" alt="">
      <div style="top: -30px; right:0" class="text-light posa fow ">
        <img ref="ar_1" id='ar_2' width="20" src="assets/el_arrow.svg" fill='blue' alt="">
        <img ref="ar_2" id="ar_2" width="20" src="assets/el_arrow.svg" alt="">
        <img ref='ar_3' id="ar_2" width="20" src="assets/el_arrow.svg" alt="">

      </div>
    </div>
    <p style='color: #37BED4' class="text-flicker-in-glow">
      Join us in the community!
    </p>
    <div class=" f-32 overflow-none">

      <span ref="tittle_text" class="fw-bold text-light">
        <span style="transition: all 500ms ease;" class="pore d-inline-block" v-for="i in tittle.split('')">
        <p style="opacity:0;" class="text-light">
          {{i}}
        </p>
        <p id="#text" class="top-left posa full" style="transition: all 500ms ease">
          {{i}}
        </p>
      </span>

        <span ref="f_tittle_free" style='color:#6AA1FE' class="mx-2 ">
          <span style="transition: all 300ms ease" class="m-0 p-0" v-for="j in tittle_free.split('')">{{j}}</span>
        </span>
      </span>
    </div>
    <div class="my-2"></div>
    <div class="fow gap-3 z-1 pore">
      <a id="b_1" class='sh no_deco rounded-3 p-2 px-3 flex-grow-1 text-center' >Join Us</a>
      <a style="color: black" id="b_2" class="fw-bold no_deco p-2 px-3 rounded-3 flex-grow-1 text-center" href="#normal_games">Explore</a>
    </div>
  </div>

</template>
<!-- -->

<script setup>
  import {
    useTemplateRef,
    ref,
    onMounted,
    onUnmounted
  } from 'vue'

  const tittle = "Play.Thousand.Of.Games.For"
  const tittle_free = "FREE"
  const tittle_text_container = useTemplateRef("tittle_text")
  const f_tittle_free = useTemplateRef("f_tittle_free")
  const block = useTemplateRef('block')
  //await, cool stuf, but the function use this need to be in async.
  const timer = s => new Promise(res => setTimeout(res, s* 1000))
  const arrows = [useTemplateRef('ar_1'), useTemplateRef('ar_2'), useTemplateRef('ar_3')]

  //don't forget to check if useTemplateRef.value is null, otherwise it'll throw error.
  async function arrow_blink() {

    for (let i of arrows) {
      if (i.value == null) {
        //console.log('koong 1 boz')
        return
      }
      i.value.classList.add('arrow-light')
      await timer(1)
      if (i.value == null) {
        //console.log('kosong 2 boz')
        return
      }
      i.value.classList.remove('arrow-light')
    }
  }

  async function play_tittle_anim() {
    for (let i = 0; i < tittle.length; i++) {
      var __item = tittle_text_container.value
      if (__item == null) {
        return
      }
      __item= __item.children.item(i).children.item(1)

      if (__item.textContent == ' ') {
        continue
      }
      __item.classList.add('scale-a-bit')
      await timer(0.15)
      if (__item == null) {
        return
      }
      __item.classList.remove('scale-a-bit')

    }

    for (let i = 0; i < tittle_free.length; i++) {
      var __item = f_tittle_free.value
      if(__item==null){
        return
      }
      
      __item= __item.children.item(i)
      __item.classList.add('text-light')
      if(__item==null){
        return
      }
      await timer(0.1)
      __item.classList.remove('text-light')
    }
  }

  async function block_fade() {
    if (block.value == null) {
      return
    }
    block.value.classList.add('block-fade')
    await timer(2)
    if (block.value == null) {
      return
    }
    block.value.classList.remove('block-fade')

  }

  onMounted(()=> {
    
    //hide .
    for (let i = 0; i < tittle.length; i++) {
      var __item = tittle_text_container.value.children.item(i).children.item(1)
      if(__item==null){
        return
      }
      if (__item.textContent == ".") {
        __item.classList.add('hide')
      }
    }
    play_tittle_anim()
    
    setInterval(()=>{
      play_tittle_anim()
    }, 10000)
    
    setInterval(
      ()=> {
        arrow_blink()
      },
      3000
    )

    setInterval(()=> {
      block_fade()}, 4000)

  })

</script>


<style scoped>
  .scale-a-bit {
    font-size: 44px;
  }

  .hide {
    display: none!important
  }
  .arrow-light {
    filter: brightness(0) saturate(100%) invert(58%) sepia(36%) saturate(991%) hue-rotate(186deg) brightness(101%) contrast(99%)!important

  }

  .arrow-mute {
    filter: brightness(0) saturate(100%) invert(38%) sepia(8%) saturate(2876%) hue-rotate(194deg) brightness(94%) contrast(92%);
  }

  .block-fade {
    opacity: 0.3
  }


</style>