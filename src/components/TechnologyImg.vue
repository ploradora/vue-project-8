<template>
  <transition name="stage">
    <div class="image-stage">
      <img class="landscape" :src="stage.imgLandscape" alt="" />
      <img class="portrait" :src="stage.imgPortrait" alt="" />
    </div>
  </transition>
</template>

<script>
export default {
  props: ["stage"],
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
.stage-enter-active {
  transition: all 0.4s ease-in-out;
}
.stage-leave-active {
  transition: unset;
}
.stage-enter-from {
  opacity: 0;
  transform: translateY(-40px);
}
.stage-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.stage-leave-from {
  opacity: 0;
  transform: unset;
}
.image-stage {
  height: 100%;
  width: 100%;
  .portrait {
    display: none;
  }
  img {
    height: 100%;
    width: 100%;
    display: block;
    object-fit: cover;
    object-position: center;
  }
  @include desktop {
    display: flex;
    align-items: center;
    justify-content: center;
    .landscape {
      display: none;
    }
    .portrait {
      display: unset;
    }
    img {
      display: block;
      height: unset;
    }
  }
}
</style>
