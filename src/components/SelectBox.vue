<template>
  <div class="select-box">
    <div class="label">
      {{ label }}
    </div>

    <div class="select-wrapper" v-on-clickaway="onClickaway">
      <div class="select-selected" @click="toggleOpen">
        {{ selectedValue }}
      </div>

      <div class="select-items" :class="{ show: showOptions }">
        <div class="item-wrapper">
          <div
            v-for="option in options"
            :key="option"
            :class="{ [option.toLowerCase()]: true }"
            class="option"
            @click="selectOption(option)"
          >
            {{ option }}
          </div>
        </div>
      </div>

      <div class="chevron">
        <i class="chevron-down" />
      </div>
    </div>
  </div>
</template>

<script>
import { mixin as clickaway } from "vue-clickaway";
export default {
  mixins: [clickaway],
  props: {
    value: String,
    options: Array,
    label: String
  },
  data() {
    return {
      showOptions: false,
      selectedValue: "Original"
    };
  },
  beforeMount() {
    this.selectedValue = this.value;
  },
  watch: {
    value(newVal) {
      if (newVal !== this.selectedValue) {
        this.selectedValue = newVal;
      }
    }
  },
  methods: {
    toggleOpen() {
      this.showOptions = !this.showOptions;
    },
    onClickaway() {
      this.showOptions = false;
    },
    selectOption(option) {
      this.selectedValue = option;
      this.showOptions = false;
      this.$emit("input", this.selectedValue);
    }
  }
};
</script>

<style lang="scss">
.select-box {
  display: flex;
  flex-direction: row;

  .label {
    text-align: left;
    text-transform: capitalize;
    width: 80px;
    line-height: 40px;
  }

  .select-wrapper {
    position: relative;
    width: 250px;
    height: 40px;
  }

  .select-selected,
  .option {
    font-size: 24px;
    line-height: 40px;
  }

  .chevron {
    position: absolute;
    right: 0;
    top: 0;
    bottom: 0;
    width: 16px;
    padding: 9px 14px;
    pointer-events: none;

    i.chevron-down {
      display: block;
      border-right: 3px solid black;
      border-bottom: 3px solid black;
      transform: rotateZ(45deg);
      width: 12px;
      height: 12px;
      transition: 200ms ease-in-out transform;
    }
  }

  .select-items.show ~ .chevron .chevron-down {
    transform: rotateZ(-135deg) translateY(-3px) translateX(-5px);
  }

  .select-selected {
    color: black;
    background-color: white;
    font-size: 24px;
    line-height: 40px;

    border: 1px solid;
    border-color: #eaf1f1 #e4eded #dbe7e7 #e4eded;
    border-radius: 4px;

    height: 100%;
    cursor: pointer;
  }

  .select-items {
    display: none;
    position: absolute;
    background-color: white;
    top: 100%;
    left: 0;
    right: 0;
    z-index: 99;
    overflow: hidden;

    border: 1px solid;
    border-color: #eaf1f1 #e4eded #dbe7e7 #e4eded;
    border-radius: 4px;

    .option {
      border-bottom: 1px solid #0000001a;
      cursor: pointer;

      &.arceuus:hover {
        background-color: #755a9e33;
      }
      &.piscarilius:hover {
        background-color: #82a2c133;
      }
      &.lovakengj:hover {
        background-color: #c5941833;
      }
      &.shayzien:hover {
        background-color: #a8433c33;
      }
      &.hosidius:hover {
        background-color: #3d6e3f33;
      }
      &.kourend:hover {
        background-color: #e0dbdb33;
      }
      &.brimhaven:hover {
        background-color: #4a4c8533;
      }
      &.original:hover {
        background-color: #cec9b533;
      }
      &:hover {
        background-color: #0000001a;
      }
    }

    &.show {
      display: block;
    }
  }
}
</style>
