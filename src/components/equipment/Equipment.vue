<template>
  <div class="equipment">
    <osrs-popup-box
      :options="options"
      ref="popupBox"
      @click="popupOptionSelect"
    />

    <div class="interface">
      <div class="background">
        <img src="/img/Interface/eq_screen.png" alt="Equipment screen" />
      </div>

      <equip-slot
        v-for="(colour, part) in colours"
        :key="part"
        :part="part"
        :colour="colour"
        @click="handleClick($event, part)"
      />
    </div>
  </div>
</template>

<script>
import OsrsPopupBox from "../OsrsPopupBox";
import EquipSlot from "./EquipSlot";

export default {
  components: { OsrsPopupBox, EquipSlot },
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
  },
  data() {
    return {
      showOptions: false,
      options: [],
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
  mounted() {
    document.documentElement.addEventListener(
      "click",
      this.clickawayHandler,
      false
    );
  },
  beforeDestroy() {
    document.documentElement.removeEventListener(
      "click",
      this.clickawayHandler,
      false
    );
  },
  methods: {
    handleClick(event, part) {
      this.options = this.generateOptions(part);
      const menu = this.$refs.popupBox;
      if (menu) {
        menu.showMenu(event, part);
      }
    },
    generateOptions(part) {
      if (part === "head") {
        part = "hood";
      }
      return this.colourList.map(colour => {
        return {
          key: colour,
          html: `Equip <span class="highlight ${colour.toLowerCase()}">${colour}</span> <span class="highlight">${part}</span>`
        };
      });
    },
    popupOptionSelect(colour, part) {
      this.$emit("select", colour, part);
    },
    closePopup() {
      const menu = this.$refs.popupBox;
      if (menu) {
        menu.hideMenu();
      }
    },
    clickawayHandler(event) {
      const path =
        event.path || (event.composedPath ? event.composedPath() : undefined);
      if (path && path.indexOf(this.$el) < 0) {
        this.closePopup();
      }
    }
  }
};
</script>

<style lang="scss">
.equipment {
  position: relative;
  width: 160px;
  height: 211px;
}

.equipment .interface {
  .background {
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
  }

  .head,
  .body,
  .legs,
  .boots,
  .cape,
  .gloves {
    position: absolute;
  }

  .head {
    left: 62px;
    top: 8px;
  }

  .body {
    left: 62px;
    top: 86px;
  }

  .legs {
    left: 62px;
    top: 126px;
  }

  .boots {
    left: 62px;
    top: 166px;
  }

  .cape {
    left: 21px;
    top: 47px;
  }

  .gloves {
    left: 6px;
    top: 166px;
  }
}
</style>
