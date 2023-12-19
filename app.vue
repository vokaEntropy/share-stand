<template>
  <div class="app">
    <button @click="mobileShare">Share only text (with opengraph)</button>
    <button @click="imageShare">Share with image in url</button>
    <button @click="imageShareByFiles">Share with image by files</button>
    <button @click="imageShareByAll">Share with image by all</button>
    <button @click="mobileImageShare">Share text + image link</button>
    <button @click="doubleShareFiles">Share double</button>
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

const imageShare = async () => {
  if (process.client) {
    var data = {
      title: 'Привет',
      text: 'Посмотрите на эту картинку!',
      url: 'data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMDAxO3d9P/wAARCAAKAAoDASIAAhEBAxEB/8QAFwABAQEBAAAAAAAAAAAAAAAAAAAAf/xAAUEAEAAAAAAAAAAAAAAAAAAAAA/9oADAMBAAIQAxAAAAHx0Y29tLm9uZw==',
    };


    try {
      await navigator.share(data);
    } catch (err) {
      console.error("Share failed:", err);
    }
  }
};

const imageShareByFiles = async () => {
  if (process.client) {
    const image = 'https://pixabay.com/get/g9fc4d3e4814bdb2fa594241ba28676b33e0af7ca604b54987076921b7844524e0ef37be07bb28d0957b0718892fb9cc57a132fd251141dc389d53b1bdd6cf847_640.jpg'
    const imageResponse = await fetch(image);
    const imageBlob = await imageResponse.blob();
    const imageFile = new File([imageBlob], "image.jpg", { type: imageBlob.type });

    try {
      await navigator.share({
        files: [imageFile],
        title: "Поймай дракона, получи предсказание",
        text: "Поймай дракона, получи предсказание",
      });
    } catch (err) {
      console.error("Share failed:", err);
    }
  }
};

const imageShareByAll = async () => {
  if (process.client) {
    const image = 'https://pixabay.com/get/g9fc4d3e4814bdb2fa594241ba28676b33e0af7ca604b54987076921b7844524e0ef37be07bb28d0957b0718892fb9cc57a132fd251141dc389d53b1bdd6cf847_640.jpg'
    const imageResponse = await fetch(image);
    const imageBlob = await imageResponse.blob();
    const imageFile = new File([imageBlob], "image.jpg", { type: imageBlob.type });

    try {
      await navigator.share({
        title: "Поймай дракона, получи предсказание",
        text: "Поймай дракона, получи предсказание",
        url: "data:text/plain,%23тылучший",
        files: [imageFile],
      });
    } catch (err) {
      console.error("Share failed:", err);
    }
  }
};

const mobileImageShare = async () => {
  if (process.client) {
    const image = 'https://thefastest.megafon.ru/images/og/dragon.jpg'

    const text = `'Поймай дракона, получи предсказание'\n\n#МегаФон2024\nhttps://thefastest.megafon.ru\n\n${image}`;

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

const doubleShareFiles = async () => {
  if (process.client) {
    const image = 'https://pixabay.com/get/g9fc4d3e4814bdb2fa594241ba28676b33e0af7ca604b54987076921b7844524e0ef37be07bb28d0957b0718892fb9cc57a132fd251141dc389d53b1bdd6cf847_640.jpg'
    const imageResponse = await fetch(image);
    const imageBlob = await imageResponse.blob();
    const imageFile = new File([imageBlob], "image.jpg", { type: imageBlob.type });

    try {
      await navigator.share({
        title: "Поймай дракона, получи предсказание",
        text: "Поймай дракона, получи предсказание",
      });
      await navigator.share({
        files: [imageFile],
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
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}
</style>
