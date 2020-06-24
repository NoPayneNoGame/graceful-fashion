<template>
  <div class="graceful">
    <outfit-piece
      v-for="(colour, part) in colours"
      :key="part"
      :part="part"
      :colour="colour"
    />
  </div>
</template>

<script>
import OutfitPiece from "./OutfitPiece";

export default {
  components: { OutfitPiece },
  props: {
    colours: {
      type: Object,
      default: () => ({
        head: "Original",
        body: "Original",
        gloves: "Original",
        legs: "Original",
        boots: "Original",
        cape: "Original"
      })
    }
  }
};
</script>

<style lang="scss">
.graceful {
  position: relative;
  min-width: 300px;
  margin-top: 5%;

  img {
    position: absolute;
    left: 0;
    top: 0;
  }
}
</style>
