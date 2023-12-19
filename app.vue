<template>
  <div class="app">
    <button @click="mobileShare">Share msg</button>
  </div>
</template>

<script setup>
const mobileShare = async () => {
  if (process.client) {
    const image = 'https://thefastest.megafon.ru/images/og/dragon.jpg'

    const text = `'Поймай дракона, получи предсказание'\n\n#МегаФон2024\nhttps://thefastest.megafon.ru`;

    try {
      await navigator.share({
        title: "Поймай дракона, получи предсказание",
        text,
      });
    } catch (err) {
      console.error("Share failed:", err);
    }
  }
};
</script>

<style scoped>
.app {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
