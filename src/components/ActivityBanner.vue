<template>
  <div
    class="activities__banner"
    :style="{ backgroundColor: banners[index].background }"
  >
    <img
      :src="banners[index].name"
      :alt="'icon ' + banners[index].alt"
      class="activities__banner__icon"
    />
  </div>
</template>

<script>
export default {
  props: {
    index: {
      type: Number,
      required: true,
    },
  },
  setup() {
    const banners = [
      {
        name: require("@/assets/icon-work.svg"),
        alt: "exercise",
        id: "0",
        background: "#ff8c66",
      },
      {
        name: require("@/assets/icon-play.svg"),
        alt: "play",
        id: "1",
        background: "#56c2e6",
      },
      {
        name: require("@/assets/icon-study.svg"),
        alt: "self-care",
        id: "2",
        background: "#ff5c7c",
      },
      {
        name: require("@/assets/icon-exercise.svg"),
        alt: "social",
        id: "3",
        background: "#4acf81",
      },
      {
        name: require("@/assets/icon-social.svg"),
        alt: "study",
        id: "4",
        background: "#7536d3",
      },
      {
        name: require("@/assets/icon-self-care.svg"),
        alt: "work",
        id: "5",
        background: "#f1c65b",
      },
    ];
    return { banners };
  },
};
</script>

<style>
.activities__banner {
  position: relative;
  height: 68px;
  top: 20px;
  border-radius: 15px 15px 0 0;
  overflow: hidden;
  z-index: -1;
}
.activities__banner__icon {
  position: absolute;
  right: 22px;
  top: -8px;
  height: 80px;
}
</style>
