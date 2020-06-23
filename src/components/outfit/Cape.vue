<template>
  <div class="outfit-piece">
    <img :src="imgSrc" :alt="alt" />
  </div>
</template>

<script>
export default {
  props: {
    colour: {
      type: String
    }
  },
  computed: {
    imgSrc() {
      return `/img/${this.colour}/cape.png`;
    },
    alt() {
      return `${this.colour} Cape`;
    }
  }
};
</script>
