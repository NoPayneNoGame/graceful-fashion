<template>
  <div class="graceful">
    <hat :colour="colours.head" />
    <chest :colour="colours.body" />
    <gloves :colour="colours.gloves" />
    <legs :colour="colours.legs" />
    <boots :colour="colours.boots" />
    <cape :colour="colours.cape" />
  </div>
</template>

<script>
import Boots from "./outfit/Boots";
import Cape from "./outfit/Cape";
import Chest from "./outfit/Chest";
import Gloves from "./outfit/Gloves";
import Hat from "./outfit/Hat";
import Legs from "./outfit/Legs";

export default {
  components: { Boots, Cape, Chest, Gloves, Hat, Legs },
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

  img {
    position: absolute;
    left: 0;
    top: 0;
  }
}
</style>
