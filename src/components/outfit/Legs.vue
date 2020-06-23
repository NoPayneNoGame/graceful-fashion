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
      return `/img/${this.colour}/legs.png`;
    },
    alt() {
      return `${this.colour} Legs`;
    }
  }
};
</script>
