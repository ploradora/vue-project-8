<template>
  <transition name="description-text">
    <div class="text-content" v-show="currentIndex === index">
      <h2 class="name">{{ location.name }}</h2>
      <p class="description">
        {{ location.description }}
      </p>
      <div class="info">
        <div class="distance-container">
          <p class="info-header">AVG. DISTANCE</p>
          <p class="distance">{{ location.distance }}</p>
        </div>
        <div class="duration-container">
          <p class="info-header">EST. TRAVEL TIME</p>
          <p class="duration">{{ location.time }}</p>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: ["location", "currentIndex", "index"],
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
.description-text-enter-active {
  transition: all 0.5s ease-out;
}

.description-text-leave-active {
  transition: unset;
}

.description-text-enter-from {
  opacity: 0;
  transform: translateY(-40px);
}
.description-text-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.description-text-leave-from {
  opacity: 0;
}
.description-text-leave-to {
  opacity: 0;
  transform: unset;
}
.text-content {
  .name {
    font-family: "Bellefair", serif;
    font-weight: 100;
    font-size: 56px;
    color: #fff;
  }
  //   .main-text-enter-active,
  //   .main-text-leave-active {
  //     transition: all 0.2s ease-in-out;
  //   }
  //   .main-text-enter-from {
  //     transform: translateX(-200px);
  //     opacity: 0;
  //   }
  //   .main-text-leave-to {
  //     transform: translateX(200px);
  //     opacity: 1;
  //   }
  .description {
    width: 85%;
    max-width: 621px;
    margin: auto;
    margin-bottom: 30px;
    max-width: 573px;
    line-height: 25px;
    font-family: "Barlow", sans-serif;
    font-size: 15px;
    color: rgba(208, 214, 249);
  }
  .info {
    width: 90%;
    margin: auto;
    max-width: 573px;
    padding-top: 30px;
    border-top: 1px solid rgba(56, 59, 75, 100%);
    .info-header {
      margin-bottom: 15px;
      font-family: "Barlow Condensed", sans-serif;
      font-size: 14px;
      letter-spacing: 2.36px;
      color: rgba(208, 214, 249);
    }
    .distance-container {
      margin-bottom: 35px;
    }
    .distance,
    .duration {
      font-family: "Bellefair", serif;
      font-size: 28px;
      color: #fff;
    }
  }
  @include tablet {
    .name {
      font-size: 80px;
    }
    .description {
      width: 85%;
      max-width: 563px;
      line-height: 25px;
      font-family: "Barlow", sans-serif;
      font-size: 15px;
      color: rgba(208, 214, 249);
    }
    .info {
      display: flex;
      align-items: center;
      justify-content: center;
      .distance-container {
        margin-bottom: unset;
        margin-right: 100px;
      }
    }
  }
  @include desktop {
    .name {
      font-size: 100px;
    }
    .description {
      margin: unset;
      width: unset;
      margin-bottom: 30px;
      max-width: unset;
      line-height: 32px;
      font-family: "Barlow", sans-serif;
      font-size: 18px;
      color: rgba(208, 214, 249);
    }
    .info {
      margin: unset;
      width: unset;
      display: flex;
      align-items: center;
      justify-content: start;
      .distance-container {
        margin-bottom: unset;
        margin-right: 60px;
      }
    }
  }
}
</style>
