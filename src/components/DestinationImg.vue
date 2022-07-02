<template>
  <transition name="image-slide">
    <div class="location-image">
      <img
        v-show="currentIndex === index"
        :src="image.img"
        :alt="image.alt"
      />
    </div>
  </transition>
</template>

<script>
export default {
  props: ["currentIndex", 'image', 'index'],
  data() {
    return {
    //   images: [
    //     {
    //       img: require("../assets/destination/image-moon.png"),
    //       alt: "the moon",
    //     },
    //     {
    //       img: require("../assets/destination/image-mars.png"),
    //       alt: "mars",
    //     },
    //     {
    //       img: require("../assets/destination/image-europa.png"),
    //       alt: "europa moon",
    //     },
    //     {
    //       img: require("../assets/destination/image-titan.png"),
    //       alt: "titan moon",
    //     },
    //   ],
    };
  },
};
</script>

<style scoped lang="scss">
@mixin tablet {
  @media only screen and(min-width: 551px) {
    @content;
  }
}
@mixin desktop {
  @media only screen and(min-width: 900px) {
    @content;
  }
}
.image-slide-enter-active {
  transition: all 0.2s linear;
}

.image-slide-leave-active {
  transition: unset;
}
.image-slide-enter-from {
  opacity: 0;
  transform: translateX(-400px);
}
.image-slide-enter-to {
  opacity: 1;
  transform: translateX(0);
}
.image-slide-leave-from {
  opacity: 0;
}
.image-slide-leave-to {
  opacity: 0;
  transform: translateX(400px);
}
.location-image {
  margin-top: 35px;
  margin-bottom: 35px;
  width: 100%;
  height: fit-content;
  overflow: hidden;

  img {
    width: 50%;
  }
  @include tablet {
    margin-top: 45px;
    img {
      max-width: 300px;
    }
  }
  @include desktop {
    width: unset;
    margin-top: unset;
    margin-bottom: unset;
    display: grid;
    place-items: center;
    max-width: 650px;
    flex-basis: 50%;
    img {
      width: 70%;
      max-width: 445px;
    }
  }
}
</style>
