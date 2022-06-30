<template>
  <nav :class="{ fullHeight: mobileMenu }">
    <div class="nav-wrapper">
      <router-link @click="closeMenu" :to="{ name: 'home' }"
        ><img class="logo-nav" src="./assets/shared/logo.svg" alt="logo icon"
      /></router-link>

      <img
        v-if="menuIcon"
        @click="openMenu"
        class="menu-mobile"
        src="./assets/shared/icon-hamburger.svg"
        alt="menu icon"
      />
      <div
        @click="closeMenu"
        class="overlay"
        :class="{ animateOverlay: mobileMenu }"
      ></div>
      <div class="nav-menu" :class="{ animate: mobileMenu }">
        <img
          @click="closeMenu"
          class="close-menu"
          src="./assets/shared/icon-close.svg"
          alt="close icon"
        />
        <div class="nav-links">
          <router-link @click="closeMenu" :to="{ name: 'home' }"
            ><span>00</span>HOME</router-link
          >
          <router-link @click="closeMenu" :to="{ name: 'destination' }"
            ><span>01</span>DESTINATION</router-link
          >
          <router-link @click="closeMenu" :to="{ name: 'crew' }"
            ><span>02</span>CREW</router-link
          >
          <router-link @click="closeMenu" :to="{ name: 'technology' }"
            ><span>03</span>TECHNOLOGY</router-link
          >
        </div>
      </div>
    </div>
  </nav>
  <router-view />
</template>

<script>
export default {
  data() {
    return {
      mobileMenu: false,
      menuIcon: true,
    };
  },
  mounted() {
    this.resizeWindow();
    window.addEventListener("resize", this.resizeWindow);
  },
  methods: {
    openMenu() {
      this.mobileMenu = true;
      this.menuIcon = false;
      document.body.style.overflow = "hidden";
    },
    closeMenu() {
      this.mobileMenu = false;
      this.menuIcon = true;
      document.body.style.overflow = "unset";
    },
    resizeWindow() {
      const width = window.innerWidth;
      if (width >= 551) {
        this.mobileMenu = true;
        document.body.style.overflow = "unset";
      } else {
        this.mobileMenu = false;
        this.menuIcon = true;
        document.body.style.overflow = "unset";
      }
    },
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
.fullHeight {
  min-height: 100vh;
  @include tablet {
    min-height: unset;
  }
}
nav {
  position: absolute;
  width: 100%;
  font-weight: bold;
  color: #2c3e50;
  overflow: hidden;
  .nav-wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 24px;
    .logo-nav {
      width: 40px;
      cursor: pointer;
    }
    .menu-mobile {
      cursor: pointer;
    }
    .nav-menu {
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      display: flex;
      flex-direction: column;
      width: 68%;
      min-height: 100vh;
      transform: translateX(100%);
      background-color: rgba(66, 66, 66, 0.397);
      backdrop-filter: blur(10px);
      opacity: 0;
      z-index: 10;
      .close-menu {
        align-self: end;
        width: 19.09px;
        margin-top: 34px;
        margin-right: 26px;
        margin-bottom: 48px;
        cursor: pointer;
      }
      .nav-links {
        padding-left: 32px;
        display: flex;
        flex-direction: column;
        font-family: "Barlow Condensed", sans-serif;
        a {
          font-weight: 100;
          text-decoration: none;
          padding: 8px 0;
          margin: 8px 0;
          letter-spacing: 2.7px;
          color: #fff;
          cursor: pointer;
          span {
            font-weight: 800;
            width: 1rem;
            display: inline-block;
            font-size: 16px;
            margin-right: 11px;
          }
          &:hover {
            transition: all 0.15s linear;
            box-shadow: inset -3px 0 rgba(255, 255, 255, 0.5);
          }
        }
        .router-link-exact-active {
          box-shadow: inset -3px 0 #fff;
        }
      }
    }
    .animate {
      min-height: 100vh;
      transform: unset;
      opacity: 1;
      transition: all 0.15s ease-in-out;
    }
    .overlay {
      width: 100%;
      min-height: 100vh;
      position: absolute;
      top: 0;
      left: 0;
      transform: translateX(100%);
      opacity: 0;
      background-color: rgba(154, 199, 235, 0);
      z-index: 8;
      cursor: pointer;
    }
    .animateOverlay {
      transform: unset;
      opacity: 1;
      z-index: 8;
      transition: all 0.15s ease-in-out;
    }
  }
  @include tablet {
    padding: unset;
    .nav-wrapper {
      padding: unset;
      padding-left: 40px;
      .menu-mobile,
      .overlay {
        display: none;
      }
      .logo-nav {
        width: 48px;
      }
      .nav-menu {
        min-height: unset;
        transform: unset;
        opacity: unset;
        position: relative;
        width: 80%;
        max-width: 453px;
        .close-menu {
          display: none;
        }
        .nav-links {
          flex-direction: row;
          justify-content: space-between;
          padding: 0 40px;
          a {
            padding: 35px 0;
            margin-bottom: unset;

            span {
              display: none;
            }
            &:hover {
              box-shadow: inset 0 -3px rgba(255, 255, 255, 0.5);
            }
          }
          .router-link-exact-active {
            box-shadow: inset 0 -3px #fff;
          }
        }
      }
      .animate,
      .animateOverlay {
        opacity: unset;
        transform: unset;
        transition: unset;
      }
    }
  }
  @include desktop {
    padding: 20px 0;
    .nav-wrapper {
      position: relative;
      .nav-menu {
        max-width: unset;
        background-color: unset;
        backdrop-filter: unset;
        width: 92%;
        flex-direction: row;
        justify-content: flex-end;
        overflow: hidden;
        .nav-links {
          width: 80%;
          max-width: 800px;
          position: relative;
          padding-left: 55px;
          padding-right: 70px;
          justify-content: space-around;
          background-color: rgba(43, 44, 44, 0.274);
          backdrop-filter: blur(10px);
          &::after {
            position: absolute;
            content: "";
            top: 50%;
            left: -96%;
            transform: translateY(-50%);
            height: 1px;
            width: 100%;
            background-color: rgba(255, 255, 255, 0.336);
          }
          a {
            padding: 40px 0;
            span {
              display: unset;
            }
          }
        }
      }
    }
  }
}
</style>
