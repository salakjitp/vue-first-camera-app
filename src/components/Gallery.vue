<template>
  <div class="gallery gallery-display py-5">
      <canvas></canvas>
  </div>
</template>

<script>
export default {
    name: 'gallery'
}
</script>

<style lang="scss" scoped>
.gallery-display{
    // display: block;
    width: 100%;
    height: 100vh;

    // padding: 25px;
    box-sizing: border-box;

    canvas{
        display: block;
        width: 100%;
        max-width: 1280px;
        margin: 0 auto;

        box-shadow: 4px 4px 12px 0px; // transparentize($color: 171717, $amount : 0.75);
    }
}
</style>