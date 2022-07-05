<template>
  <div class="technology">
    <div class="technology-content">
      <p><span>03</span>SPACE LAUNCH 101</p>
      <div class="stages">
        <div class="image-container">
          <technology-img
            v-show="currentStage === index"
            v-for="(stage, index) in stagesImages"
            :key="index"
            :stage="stage"
          ></technology-img>
        </div>
        <div class="stages-content">
          <div class="nav-buttons">
            <button
              :class="{ active: currentStage === 0 }"
              @click="selectStage(0)"
            >
              1
            </button>
            <button
              :class="{ active: currentStage === 1 }"
              @click="selectStage(1)"
            >
              2
            </button>
            <button
              :class="{ active: currentStage === 2 }"
              @click="selectStage(2)"
            >
              3
            </button>
          </div>
          <div class="about-container">
            <p class="header">THE TERMINOLOGY…</p>
            <technology-text
              v-show="currentStage === index"
              v-for="(stage, index) in stages"
              :key="index"
              :stage="stage"
            ></technology-text>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TechnologyImg from "@/components/TechnologyImg.vue";
import TechnologyText from "@/components/TechnologyText.vue";
export default {
  components: { TechnologyImg, TechnologyText },
  data() {
    return {
      stages: [
        {
          title: "LAUNCH VEHICLE",
          about:
            "A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a payload from Earth's surface to space, usually to Earth orbit or beyond. Our WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall, it's quite an awe-inspiring sight on the launch pad!",
        },
        {
          title: "SPACEPORT",
          about:
            "A spaceport or cosmodrome is a site for launching (or receiving) spacecraft, by analogy to the seaport for ships or airport for aircraft. Based in the famous Cape Canaveral, our spaceport is ideally situated to take advantage of the Earth’s rotation for launch.",
        },
        {
          title: "SPACE CAPSULE",
          about:
            "A space capsule is an often-crewed spacecraft that uses a blunt-body reentry capsule to reenter the Earth's atmosphere without wings. Our capsule is where you'll spend your time during the flight. It includes a space gym, cinema, and plenty of other activities to keep you entertained.",
        },
      ],
      stagesImages: [
        {
          imgLandscape: require("../assets/technology/image-launch-vehicle-landscape.jpg"),
          imgPortrait: require("../assets/technology/image-launch-vehicle-portrait.jpg"),
        },
        {
          imgLandscape: require("../assets/technology/image-spaceport-landscape.jpg"),
          imgPortrait: require("../assets/technology/image-spaceport-portrait.jpg"),
        },
        {
          imgLandscape: require("../assets/technology/image-space-capsule-landscape.jpg"),
          imgPortrait: require("../assets/technology/image-space-capsule-portrait.jpg"),
        },
      ],
      currentStage: 0,
    };
  },
  mounted() {
    window.addEventListener("keydown", (e) => {
      const slide = e.code;
      if (slide === "ArrowDown") {
        if (this.stages.length - 1 <= this.currentStage) {
          this.currentStage = -1;
        }
        this.currentStage++;
      }
      if (slide === "ArrowUp") {
        if (this.currentStage <= 0) {
          this.currentStage = this.stages.length;
        }
        this.currentStage--;
      }
    });
  },
  methods: {
    selectStage(stage) {
      this.currentStage = stage;
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

.technology {
  background-image: url("../assets/technology/background-technology-mobile.jpg");
  background-repeat: no-repeat;
  background-position: center top;
  background-size: cover;
  min-height: 100vh;
  text-align: center;
  .technology-content {
    width: 100%;
    padding-top: 90px;
    > p {
      padding-bottom: 40px;
      font-family: "Barlow Condensed", sans-serif;
      font-size: 16px;
      color: #fff;
      letter-spacing: 2.7px;
      span {
        margin-right: 10px;
        font-weight: 900;
        color: rgba(255, 255, 255, 0.336);
      }
    }
    .stages {
      .image-container {
        position: relative;
        height: 170px;
        display: flex;
        align-items: center;
        justify-content: center;
        overflow: hidden;
        margin-bottom: 25px;
      }
      .stages-content {
        .nav-buttons {
          margin: auto;
          display: flex;
          align-items: center;
          justify-content: space-between;
          width: 150px;
          button {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 1px solid rgba(77, 77, 86);
            color: #fff;
            background-color: unset;
            font-family: "Bellefair", serif;
            cursor: pointer;
            &:hover {
              transition: border 0.15s linear;
              border: 1px solid #fff;
            }
          }
          .active {
            color: unset;
            border: 1px solid #fff;
            background-color: #fff;
          }
        }
        .about-container {
          margin-top: 20px;
          height: 270px;
          overflow: hidden;
          .header {
            font-family: "Barlow Condensed", sans-serif;
            letter-spacing: 2.36px;
            font-size: 14px;
            color: rgba(208, 214, 249);
            margin-bottom: 10px;
          }
        }
      }
    }
  }
  @include tablet {
    background-image: url("../assets/technology/background-technology-tablet.jpg");
    background-repeat: no-repeat;
    background-position: center top;
    background-size: cover;
    .technology-content {
      padding-top: 130px;
      padding-bottom: unset;
      max-width: unset;
      > p {
        text-align: start;
        padding-left: 40px;
        font-size: 20px;
        letter-spacing: 3.38px;
      }
      .stages {
        .image-container {
          height: 310px;
        }
        .stages-content {
          .nav-buttons {
            width: 210px;
            margin-bottom: 45px;
            button {
              font-size: 24px;
              width: 60px;
              height: 60px;
            }
          }
          .about-container {
            height: 270px;
            .header {
              letter-spacing: 2.7px;
              font-size: 16px;
              margin-bottom: 15px;
            }
          }
        }
      }
    }
  }
  @include desktop {
    background-image: url("../assets/technology/background-technology-desktop.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    text-align: unset;
    .technology-content {
      padding-top: 130px;
      padding-bottom: unset;
      max-width: unset;
      > p {
        padding-bottom: 10px;
        text-align: start;
        padding-left: 11%;
        font-size: 28px;
        letter-spacing: 4.72px;
      }
      .stages {
        display: flex;
        flex-direction: row-reverse;
        justify-content: space-between;
        align-items: center;
        padding-left: 11%;
        .image-container {
          height: 500px;
          flex-basis: 40%;
        }
        .stages-content {
          flex-basis: 60%;
          display: flex;
          align-items: center;
          margin-right: 20px;
          .nav-buttons {
            margin: unset;
            margin-bottom: unset;
            margin-right: 8%;
            flex-direction: column;
            width: 80px;
            button {
              font-size: 32px;
              width: 80px;
              height: 80px;
            }
            button:not(:last-child) {
              margin-bottom: 30px;
            }
          }
          .about-container {
            margin-top: unset;
            height: 320px;
          }
        }
      }
    }
  }
}
</style>
