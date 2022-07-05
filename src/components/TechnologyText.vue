<template>
  <transition name="stage">
    <div class="about-stage">
      <p class="title">{{ stage.title }}</p>
      <p class="description">{{ stage.about }}</p>
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
  transform: translateX(100px);
}
.stage-enter-to {
  opacity: 1;
  transform: translateX(0);
}
.stage-leave-from {
  opacity: 0;
  transform: unset;
}

.about-stage {
  margin: auto;
  width: 87%;
  .title {
    margin-bottom: 20px;
    font-family: "Bellefair", serif;
    font-size: 24px;
    color: #fff;
  }
  .description {
    max-width: 475px;
    margin: auto;
    font-size: 15px;
    line-height: 25px;
    color: rgba(208, 214, 249);
  }
  @include tablet {
    .title {
      font-size: 40px;
    }
    .description {
      max-width: 458px;
      font-size: 16px;
      line-height: 28px;
    }
  }

  @include desktop {
    margin: unset;
    width: unset;
    .title {
      font-size: clamp(30px, 3.5vw, 56px);
    }
    .description {
      max-width: 500px;
      font-size: 18px;
      line-height: 32px;
    }
  }
}
</style>
