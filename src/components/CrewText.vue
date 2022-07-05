<template>
  <transition name="crew-info">
    <div class="about-member">
      <p class="profession">{{ member.profession }}</p>
      <p class="name">{{ member.name }}</p>
      <p class="about-member">
        {{ member.about }}
      </p>
    </div>
  </transition>
</template>

<script>
export default {
  props: ["member"],
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
.crew-info-enter-active {
  transition: all 0.4s ease-in-out;
}
.crew-info-leave-active {
  transition: none;
}
.crew-info-enter-from {
  opacity: 0;
  transform: translateX(50px);
}
.crew-info-enter-to {
  opacity: 1;
  transform: translateX(0);
}
.crew-info-leave-from {
  opacity: 0;
  transform: none;
}
.about-member {
  .profession {
    margin-bottom: 10px;
    font-family: "Bellefair", serif;
    color: rgba(151, 151, 151, 0.7);
  }
  .name {
    margin-bottom: 10px;
    font-family: "Bellefair", serif;
    font-size: 24px;
    color: #fff;
  }
  .about-member {
    font-family: "Barlow", sans-serif;
    line-height: 25px;
    color: rgba(208, 214, 249);
  }
  @include tablet {
    .profession {
      font-size: 24px;
    }
    .name {
      font-size: 40px;
    }
    .about-member {
      line-height: 28px;
    }
  }
  @include desktop {
    .profession {
      font-size: 32px;
    }
    .name {
      //   font-size: 56px;
      font-size: clamp(30px, 5vw, 56px);
      margin-bottom: 30px;
    }
    .about-member {
      font-size: 18px;
      line-height: 32px;
      max-width: 444px;
    }
  }
}
</style>
