<template>
  <div class="home">
    <div class="colour-picker">
      <div class="colour" v-for="(value, key) in chosenColours" :key="key">
        <select-box
          v-model="chosenColours[key]"
          :label="key"
          :options="colourList"
        />
      </div>
    </div>

    <graceful :colours="chosenColours" />
  </div>
</template>

<script>
import SelectBox from "@/components/SelectBox";
import Graceful from "@/components/Graceful";

export default {
  name: "Home",
  components: { Graceful, SelectBox },
  props: {
    msg: String
  },
  data() {
    return {
      chosenColours: {
        head: "Original",
        body: "Original",
        gloves: "Original",
        legs: "Original",
        boots: "Original",
        cape: "Original"
      },
      colourList: [
        "Arceuus",
        "Brimhaven",
        "Hosidius",
        "Kourend",
        "Lovakengj",
        "Original",
        "Piscarilius",
        "Shayzien"
      ]
    };
  }
};
</script>

<style lang="scss">
.home {
  display: flex;
  justify-content: space-around;
  width: 100%;

  .colour-picker {
    margin: 64px 0;
  }
  .colour {
    padding: 16px 8px;
  }
}
</style>
