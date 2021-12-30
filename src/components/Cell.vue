<template>
  <button @click="toggleSelection" @keydown.enter="toggleSelection"
          :class="{ selected: isSelected }">
    {{ this.word }}
  </button>
</template>

<script>
export default {
  name: 'CellButton',
  data() {
    return {
      isSelected: false,
    };
  },
  props: {
    word: {
      type: String,
      default: 'x',
    },
  },
  methods: {
    toggleSelection() {
      this.isSelected = !this.isSelected;
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  cursor: pointer;
  border: 5px solid #15d09a;
  border-radius: 35px;
  width: 100px;
  height: 100px;
  background: transparent;
  transition: all 0.2s cubic-bezier(0.785, 0.135, 0.15, 0.86);
  &.selected {
    background: aquamarine;
  }
  &:focus {
    border-color: #fc8904;
    outline: 0;
  }
}
</style>
