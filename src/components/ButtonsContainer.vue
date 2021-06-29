<template>
  <div
    id="button-container"
    class="rounded d-flex flex-column mt-2 align-items-start"
  >
    <button
      v-for="(button, index) in buttons"
      :key="index"
      class="btn"
      :class="colors[index]"
      @click="createQuery(button, index)"
      v-show="
        (buttons[index] !== 'Where' && buttons[index] !== 'Order') ||
          (buttons[index] === 'Where' &&
            selectedColumnForSelect !== '' &&
            (currentBlocks[currentBlocks.length - 1] === 'Select' ||
              currentBlocks[currentBlocks.length - 1] === 'Delete')) ||
          (buttons[index] === 'Where' &&
            isUpdateLastInputTriggered &&
            currentBlocks[currentBlocks.length - 1] === 'Update') ||
          (buttons[index] === 'Order' &&
            selectedColumnForSelect !== '' &&
            currentBlocks[currentBlocks.length - 1] === 'Select')
      "
    >
      {{ button }}
    </button>
  </div>
</template>

<script>
export default {
  props: [
    "buttons",
    "colors",
    "clicks",
    "currentBlocks",
    "selectedColumnForSelect",
    "isUpdateLastInputTriggered",
  ],
  data() {
    return {
      newClicks: this.clicks.map((element) => {
        return element;
      }),
      newBlocks: this.currentBlocks.map((block) => {
        return block;
      }),
    };
  },
  methods: {
    createQuery(button, index) {
      if (button === "Where" || button === "Order") {
        if (button === "Where") {
          this.emitter.emit("where-clicked", [true, this.currentBlocks.length]);
        } else {
          this.emitter.emit("order-by-clicked", [
            true,
            this.currentBlocks.length,
          ]);
        }
        this.newClicks[index]++;
        this.newBlocks.push(button);
      } else if (button === "Delete") {
        this.newClicks[index]++;
        this.newClicks[1]++;
        this.newBlocks = [...this.newBlocks, button, "Where"];
      } else {
        this.newClicks[index]++;
        this.newBlocks.push(button);
      }

      this.emitter.emit("create-query", this.newClicks);
      this.emitter.emit("update-blocks", this.newBlocks);
    },
  },
  mounted() {},
};
</script>

<style scoped>
.btn {
  width: max-content;
}

#button-container {
  background-color: rgb(41, 40, 40);
}
</style>
