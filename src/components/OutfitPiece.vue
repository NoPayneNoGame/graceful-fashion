<template>
  <div class="outfit-piece">
    <img :src="imgSrc" :alt="alt" />
  </div>
</template>

<script>
export default {
  props: {
    colour: String,
    part: String
  },
  computed: {
    imgSrc() {
      return `/img/${this.colour}/${this.part}.png`;
    },
    alt() {
      return `${this.colour} ${this.part}`;
    }
  }
};
</script>
