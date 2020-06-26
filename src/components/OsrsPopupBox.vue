<template>
  <div class="osrs-box" ref="menu" :class="{ show }">
    <div class="wrapper">
      <div class="header">
        Choose Option
      </div>
      <div class="body">
        <div
          class="text"
          v-for="option in options"
          :key="option.key"
          v-html="option.html"
          @click="onClick(option.key)"
        />
        <div class="text" @click="cancel">
          Cancel
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    options: Array
  },
  data() {
    return {
      part: null,
      show: false,
      menuWidth: null,
      menuHeight: null
    };
  },
  methods: {
    showMenu(event, part) {
      this.part = part;

      const menu = this.$refs.menu;

      if (!this.menuWidth || !this.menuHeight) {
        menu.style.visibility = "hidden";
        menu.style.display = "block";
        this.menuWidth = menu.offsetWidth;
        this.menuHeight = menu.offsetHeight;
        menu.removeAttribute("style");
      }

      if (this.menuWidth + event.offsetX >= window.innerWidth) {
        menu.style.left = event.offsetX - this.menuWidth + 2 + "px";
      } else {
        menu.style.left = event.offsetX - 2 + "px";
      }

      if (this.menuHeight + event.offsetY >= window.innerHeight) {
        menu.style.top = event.offsetY - this.menuHeight + 2 + "px";
      } else {
        menu.style.top = event.offsetY - 2 + "px";
      }

      this.show = true;
    },
    hideMenu() {
      this.show = false;
    },
    onClick(colour) {
      this.hideMenu();
      this.$emit("click", colour, this.part);
    },
    cancel() {
      this.hideMenu();
      this.$emit("cancel");
    }
  }
};
</script>

<style lang="scss">
.osrs-box {
  font-family: "Runescape UF", monospace;
  font-weight: normal;
  font-style: normal;

  font-size: 16px;
  letter-spacing: 0.35px;
  text-align: left;

  display: none;
  top: 0;
  left: 0;
  position: absolute;
  z-index: 999;

  text-shadow: 1px 1px black;

  min-width: 100px;
  width: 100%;

  &.show {
    display: block;
  }

  .wrapper {
    background-color: #5d5447;
    position: relative;
    width: fit-content;
    height: fit-content;
  }

  .header {
    color: #5d5447;
    background-color: black;
    margin: 1px;
    padding: 2px;
    padding-bottom: 0;
  }

  .body {
    border: 1px solid black;
    margin: 1px;
    padding: 2px;
    padding-right: 4px;
  }

  .text {
    color: white;
    cursor: pointer;

    &:hover {
      color: #ffff00;

      .highlight.arceuus {
        color: #755a9e;
      }
      .highlight.piscarilius {
        color: #82a2c1;
      }
      .highlight.lovakengj {
        color: #c59418;
      }
      .highlight.shayzien {
        color: #a8433c;
      }
      .highlight.hosidius {
        color: #3d6e3f;
      }
      .highlight.kourend {
        color: #e0dbdb;
      }
      .highlight.brimhaven {
        color: #4a4c85;
      }
      .highlight.original {
        color: #cec9b5;
      }
    }

    .highlight {
      color: #ff9040;
    }
  }
}
</style>
