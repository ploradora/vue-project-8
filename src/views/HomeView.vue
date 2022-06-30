<template>
  <div class="home">
    <div class="text-content">
      <p class="title">SO, YOU WANT TO TRAVEL TO</p>
      <h1>SPACE</h1>
      <p class="main-text">
        Let’s face it; if you want to go to space, you might as well genuinely
        go to outer space and not hover kind of on the edge of it. Well sit
        back, and relax because we’ll give you a truly out of this world
        experience!
      </p>
    </div>
    <router-link :to="{ name: 'destination' }">
      <button>EXPLORE</button>
    </router-link>
  </div>
</template>

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
.home {
  background: url("../assets/home/background-home-mobile.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 100vh;
  text-align: center;
  padding: 112px 24px 0 24px;
  .text-content {
    z-index: 5;
    .title {
      font-family: "Barlow Condensed", sans-serif;
      font-size: 16px;
      color: rgba(208, 214, 249);
      letter-spacing: 2.7px;
    }
    h1 {
      font-family: "Bellefair", serif;
      font-weight: 100;
      font-size: 80px;
      color: #fff;
      margin-top: 20px;
      margin-bottom: 20px;
    }
    .main-text {
      margin: auto;
      max-width: 410px;
      font-family: "Barlow", sans-serif;
      font-size: 15px;
      color: rgba(208, 214, 249);
      line-height: 1.7;
    }
  }
  a {
    button {
      position: relative;
      border: none;
      width: 150px;
      height: 150px;
      border-radius: 50%;
      margin-bottom: 70px;
      align-self: center;
      font-size: 20px;
      background-color: #fff;
      letter-spacing: 1.25px;
      color: rgba(11, 13, 23);
      font-family: "Bellefair", serif;
      cursor: pointer;
      &:hover {
        transition: box-shadow 0.15s linear;
        box-shadow: 0 0 0 41px rgba(168, 168, 168, 0.322);
      }
    }
  }
  @include tablet {
    background: url("../assets/home/background-home-tablet.jpg");
    background-repeat: no-repeat;
    // background-position: 50% 85%;
    background-position: top center;
    background-size: cover;
    min-height: 100vh;
    .text-content {
      padding-top: 35px;
      .title {
        font-size: 20px;
        letter-spacing: 3.4px;
      }
      h1 {
        font-size: 90px;
        color: #fff;
        margin-top: 13px;
        margin-bottom: 7px;
      }
      .main-text {
        margin: auto;
        max-width: 415px;
        font-size: 15px;
        line-height: 1.7;
      }
    }
    button {
      width: 180px;
      height: 180px;
      margin-top: 55px;
      &:hover {
        transition: box-shadow 0.15s linear;
        box-shadow: 0 0 0 41px rgba(168, 168, 168, 0.322);
      }
    }
  }
  @include desktop {
    padding: unset;
    background: url("../assets/home/background-home-desktop.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    flex-direction: row;
    align-items: flex-end;
    min-height: 100vh;
    padding-bottom: 100px;
    padding-right: 8.5%;
    padding-left: 12%;
    .text-content {
      padding-top: unset;
      text-align: start;
      .title {
        font-size: 28px;
        letter-spacing: 4.7px;
      }
      h1 {
        font-size: 150px;
      }
      .main-text {
        margin: unset;
        max-width: 450px;
        font-size: 18px;
      }
    }
    a {
      padding-right: 20px;
      padding-bottom: 30px;
      button {
        width: 190px;
        height: 190px;
        align-self: unset;
        margin-top: unset;
        margin-bottom: unset;
      }
    }
  }
  @media only screen and (min-width: 1100px) {
    padding-left: 11%;
    a {
      padding-right: 50px;
      padding-bottom: 20px;
      button {
        width: 240px;
        height: 240px;
        &:hover {
        box-shadow: 0 0 0 60px rgba(168, 168, 168, 0.322);
      }
      }
    }
  }
}
</style>
