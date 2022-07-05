<template>
  <transition name="img">
    <div class="location-image">
      <img :src="image.img" :alt="image.alt" />
    </div>
  </transition>
</template>

<script>
export default {
  props: ["currentIndex", "image", "index"],
  data() {
    return {};
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
.img-enter-active {
  transition: all 0.5s ease-out;
}
.img-leave-active {
  transition: unset;
}
.img-enter-from {
  opacity: 0;
  transform: translateX(-50px);
}
.img-enter-to {
  opacity: 1;
  transform: translateX(0);
}
.img-leave-from {
  opacity: 0;
  transform: translateX(0);
}
.img-leave-to {
  opacity: 0;
  transform: unset;
}
.location-image {
  width: 50%;
  overflow: hidden;
  img {
    width: 100%;
    margin-top: 35px;
    margin-bottom: 35px;
  }
  @include tablet {
    max-width: 300px;
    img {
      width: 100%;
      margin-top: 25px;
      max-width: 300px;
    }
  }
  @include desktop {
    width: unset;
    margin-top: unset;
    margin-bottom: unset;
    display: flex;
    align-items: center;
    max-width: unset;
    img {
      margin: unset;
      width: 100%;
      max-width: 445px;
    }
  }
}
</style>
