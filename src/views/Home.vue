<template>
  <div class="home">
    <div class="colour-picker">
      <select-box v-model="allColour" label="Set all" :options="colourList" />
      <equipment :colours="chosenColours" @select="handleEquipChange" />
    </div>

    <graceful :colours="chosenColours" />
  </div>
</template>

<script>
import SelectBox from "@/components/SelectBox";
import Graceful from "@/components/Graceful";
import Equipment from "@/components/equipment/Equipment";

export default {
  name: "Home",
  components: { Graceful, SelectBox, Equipment },
  props: {
    msg: String
  },
  data() {
    return {
      allColour: "Original",
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
  },
  methods: {
    onClick(key) {
      this.chosenColours.head = key;
    },
    handleEquipChange(colour, part) {
      this.chosenColours[part] = colour;
    }
  },
  computed: {
    options() {
      return this.colourList.map(colour => {
        return {
          key: colour,
          html: `Equip <span class="highlight ${colour.toLowerCase()}">${colour}</span> <span class="highlight">hood</span>`
        };
      });
    }
  },
  watch: {
    allColour(newColour) {
      Object.keys(this.chosenColours).forEach(key => {
        this.chosenColours[key] = newColour;
      });
    }
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
