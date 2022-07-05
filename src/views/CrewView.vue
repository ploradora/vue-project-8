<template>
  <div class="crew">
    <div class="crew-content">
      <p><span>02</span>MEET YOUR CREW</p>
      <div class="members">
        <div class="crew-member">
          <div class="about-container">
            <crew-text
              v-show="currentMember === index"
              v-for="(member, index) in crew"
              :key="index"
              :member="member"
            >
            </crew-text>
          </div>
          <div class="nav-dots">
            <div
              @click="selectMember(0)"
              :class="{ active: currentMember === 0 }"
              class="dot"
            ></div>
            <div
              @click="selectMember(1)"
              :class="{ active: currentMember === 1 }"
              class="dot"
            ></div>
            <div
              @click="selectMember(2)"
              :class="{ active: currentMember === 2 }"
              class="dot"
            ></div>
            <div
              @click="selectMember(3)"
              :class="{ active: currentMember === 3 }"
              class="dot"
            ></div>
          </div>
        </div>
        <div class="image-container">
          <crew-img
            v-show="currentMember === index"
            v-for="(image, index) in crewImages"
            :key="index"
            :image="image"
          ></crew-img>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CrewText from "@/components/CrewText.vue";
import CrewImg from "@/components/CrewImg.vue";
export default {
  components: {
    CrewText,
    CrewImg,
  },
  data() {
    return {
      crew: [
        {
          profession: "COMMANDER ",
          name: "DOUGLAS HURLEY",
          about:
            "Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.",
        },
        {
          profession: "MISSION SPECIALIST",
          name: "MARK SHUTTLEWORTH",
          about:
            "Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.",
        },
        {
          profession: "PILOT",
          name: "VICTOR GLOVER",
          about:
            "Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.",
        },
        {
          profession: "FLIGHT ENGINEER",
          name: "ANOUSHEH ANSARI",
          about:
            "Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space. ",
        },
      ],
      crewImages: [
        {
          img: require("../assets/crew/image-douglas-hurley.png"),
          alt: "profile pircture user",
        },
        {
          img: require("../assets/crew/image-mark-shuttleworth.png"),
          alt: "profile pircture user",
        },
        {
          img: require("../assets/crew/image-victor-glover.png"),
          alt: "profile pircture user",
        },
        {
          img: require("../assets/crew/image-anousheh-ansari.png"),
          alt: "profile pircture user",
        },
      ],
      currentMember: 0,
    };
  },
  mounted() {
    window.addEventListener("keydown", (e) => {
      const slide = e.code;
      if (slide === "ArrowRight") {
        if (this.crew.length - 1 <= this.currentMember) {
          this.currentMember = -1;
        }
        this.currentMember++;
      }
      if (slide === "ArrowLeft") {
        if (this.currentMember <= 0) {
          this.currentMember = this.crew.length;
        }
        this.currentMember--;
      }
    });
  },
  methods: {
    selectMember(member) {
      this.currentMember = member;
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

.crew {
  background-image: url("../assets/crew/background-crew-mobile.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  min-height: 100vh;
  text-align: center;
  .crew-content {
    height: 100%;
    padding-top: 90px;
    width: 90%;
    max-width: 440px;
    margin: auto;
    > p {
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
    .members {
      display: flex;
      flex-direction: column-reverse;
      align-items: center;
      .crew-member {
        display: flex;
        flex-direction: column-reverse;
        align-items: center;
        .about-container {
          height: 220px;
          overflow: hidden;
        }
        .nav-dots {
          margin-bottom: 30px;
          width: 88px;
          height: 10px;
          display: flex;
          align-items: center;
          justify-content: space-between;
          .dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: rgba(151, 151, 151, 0.25);
            cursor: pointer;
            &:hover {
              transition: background-color 0.15s linear;
              background-color: rgba(151, 151, 151, 100%);
            }
          }
          .active {
            background-color: #fff;
            &:hover {
              background-color: #fff;
            }
          }
        }
      }
      .image-container {
        margin-top: 50px;
        margin-bottom: 30px;
        width: 100%;
        height: 42vh;
        display: flex;
        align-items: flex-end;
        border-bottom: 1px solid rgb(94, 94, 94);
        overflow: hidden;
      }
    }
  }
  @include tablet {
    background-image: url("../assets/crew/background-crew-tablet.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    .crew-content {
      padding-top: 130px;
      padding-bottom: unset;
      max-width: unset;
      > p {
        text-align: start;
        padding-left: 40px;
        font-size: 20px;
        letter-spacing: 3.38px;
      }
      .members {
        flex-direction: column;
        .crew-member {
          flex-direction: column;
          .about-container {
            margin-top: 35px;
            height: 200px;
            max-width: 590px;
          }
          .nav-dots {
            margin-bottom: unset;
          }
        }
        .image-container {
          margin-top: unset;
          margin-bottom: unset;
          border-bottom: unset;
          position: absolute;
          left: 50%;
          bottom: 0;
          transform: translateX(-50%);
        }
      }
    }
  }
  @include desktop {
    background-image: url("../assets/crew/background-crew-desktop.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    text-align: unset;
    .crew-content {
      margin: unset;
      width: 100%;
      > p {
        margin-bottom: unset;
        text-align: start;
        padding-left: 11%;
        font-size: 28px;
        letter-spacing: 4.72px;
      }
      .members {
        position: absolute;
        width: 100%;
        bottom: 0;
        padding-left: 11%;
        align-items: flex-end;
        flex-direction: row;
        .crew-member {
          padding-bottom: 80px;
          width: 50%;
          align-items: unset;
          .about-container {
            margin: unset;
            max-width: unset;
            height: 400px;
          }
        }
        .image-container {
          margin: unset;
          margin-top: unset;
          left: unset;
          transform: unset;
          display: unset;
          align-items: unset;
          position: unset;
          width: 50%;
          height: 68vh;
        }
      }
    }
  }
}
</style>
