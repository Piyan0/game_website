<template>
  <div main tabIndex=1 style="width: 200px; aspect-ratio: 200/180" class="fol alen pore">
    <div class="posa top_left full fow force-center z-0">
      <img style="top: -10px" width="210" src="assets/el_blur.svg" class="blur pore" alt="">
    </div>
    <div data-border style="border: 4px solid #424C83; border-bottom: 8px solid #424C83; border-radius: 10px; " class="w-100 overflow-hidden flex-grow-1 zoom-wrapper">
      <div data-image :style="{'background-image' : `url(${props.image})`}" style="transition: transform 500ms;" class="z-1 full bg-img pore">
        <div class="posa d-none full top_left">
          <div style="z-index: 1; opacity: 0.5; background-color: #5979AA; color: white" class="click rounded-3 posa full d force-center fw-bold f-48"></div>
          <div style="z-index: 3" class="posa top_left full force-center">
            <p class="f-48 text-light fw-bold">
              +
            </p>

          </div>
        </div>
      </div>
    </div>
    <div style="color: #699FF7" class=" w-100 fow jen alen gap-1 my-2 pore z-1">
      <p style="" class="f-12 text-center overflow-hidden">
        <span>
        <img style="top: -1px" class="pore " width="12" src="assets/fire.svg" alt="">
        </span>&nbsp{{
          tittle
        }}
      </p>
    </div>
  </div>

</template>
<!-- -->

<script setup>
  const props= defineProps(['tittle', 'image'])
</script>
<!-- -->

<style scoped>
  .blur{
  filter: brightness(0) saturate(100%) invert(53%) sepia(66%) saturate(951%) hue-rotate(195deg) brightness(103%) contrast(101%);
  }

  [main]:focus [data-image]{

  transform: scale(1.2);

  }
  [main]:focus [data-border]{

  border: 4px solid #699FF7!important;
  border-bottom: 8px solid #699FF7!important
  }
  @media screen and (max-width: 567px){
    [main]{
      width: 160px!important
    }
  }
  

</style>