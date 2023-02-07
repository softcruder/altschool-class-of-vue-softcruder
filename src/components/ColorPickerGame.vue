<template>
  <h1>Color Picker Game</h1>

  <div>{{ message }}</div>

  <button v-for="color in colors" :key="color" @click="matchColor(color)">
    {{ color }}
  </button>
</template>

<script>
import { ref, computed } from "@vue/composition-api";

export default {
  setup() {
    const colors = ["green", "red", "blue", "purple"];
    let message = ref("Pick a color...");

    
      // do a random color based on the array index;
      const randomNumber = computed(() => Math.floor(Math.random() * 3) + 1); //between 1 - 4
      const matchColor = (value) => {
      if (colors[randomNumber] === value) {
        message.value = `You win... [answer: ${colors[randomNumber]}]`;
        return;
      }

      message.value = `You lose [answer: ${colors[randomNumber]}]`;
    };

    return { colors, message, matchColor };
  },
};
</script>

<style></style>
