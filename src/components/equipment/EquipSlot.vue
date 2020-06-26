<template>
  <div class="equipment-slot" @click="handleClick" :class="{ [part]: true }">
    <div class="img-wrapper part-art">
      <img
        :src="`/img/Interface/${colour}/${part}.png`"
        :alt="`${colour} ${part}`"
      />
    </div>
    <div class="img-wrapper">
      <img :src="`/img/Interface/${part}.png`" :alt="`${part} slot`" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    part: String,
    colour: String
  },
  methods: {
    handleClick(event) {
      this.$emit("click", event, this.part);
    }
  }
};
</script>

<style lang="scss">
.equipment-slot {
  .img-wrapper {
    position: absolute;
    z-index: 1;
  }

  .part-art {
    z-index: 4;
    top: 0;
    left: 0;
    width: 36px;
    height: 36px;

    img {
      padding: 4px 6px;
    }
  }
}
</style>
