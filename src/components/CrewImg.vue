<template>
  <transition name="crew-img">
    <div class="image-crew">
      <img :src="image.img" :alt="image.alt" />
    </div>
  </transition>
</template>

<script>
export default {
  props: ["image"],
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
.crew-img-enter-active {
  transition: all 0.4s ease-in-out;
}
.crew-img-leave-active {
  transition: none;
}
.crew-img-enter-from {
  opacity: 0;
  transform: translateY(50px);
}
.crew-img-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.crew-img-leave-from {
  opacity: 0;
  transform: none;
}
.image-crew {
  height: inherit;
  margin: auto;
  img {
    margin: auto;
    display: block;
    height: 100%;
  }
  @include desktop {
    margin: unset;
    img {
      margin: unset;
    }
  }
}
</style>
