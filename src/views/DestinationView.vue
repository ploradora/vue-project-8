<template>
  <div class="destination">
    <div class="destination-content">
      <p><span>01</span> PICK YOUR DESTINATION</p>
      <div class="locations">
        <div class="location">
          <div class="location-item-image">
            <destination-img
              v-show="currentIndex === index"
              v-for="(image, index) in images"
              :key="image"
              :image="image"
              :index="index"
              :current-index="currentIndex"
            ></destination-img>
          </div>
          <div class="location-text">
            <div class="location-nav-buttons">
              <button
                :class="{ active: currentIndex === 0 }"
                @click="locationTo(0)"
              >
                MOON
              </button>
              <button
                :class="{ active: currentIndex === 1 }"
                @click="locationTo(1)"
              >
                MARS
              </button>
              <button
                :class="{ active: currentIndex === 2 }"
                @click="locationTo(2)"
              >
                EUROPA
              </button>
              <button
                :class="{ active: currentIndex === 3 }"
                @click="locationTo(3)"
              >
                TITAN
              </button>
            </div>
            <div class="destinations-container">
              <destination-text
                v-for="(location, index) in locations"
                :key="index"
                :location="location"
                :current-index="currentIndex"
                :index="index"
              ></destination-text>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DestinationText from "@/components/DestinationText.vue";
import DestinationImg from "@/components/DestinationImg.vue";
export default {
  components: {
    DestinationText,
    DestinationImg,
  },
  data() {
    return {
      images: [
        {
          img: require("../assets/destination/image-moon.png"),
          alt: "the moon",
        },
        {
          img: require("../assets/destination/image-mars.png"),
          alt: "mars",
        },
        {
          img: require("../assets/destination/image-europa.png"),
          alt: "europa moon",
        },
        {
          img: require("../assets/destination/image-titan.png"),
          alt: "titan moon",
        },
      ],
      locations: [
        {
          name: "MOON",
          description:
            "See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.",
          distance: "384,400 KM",
          time: "3 DAYS",
        },
        {
          name: "MARS",
          description:
            "Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!",
          distance: "225 MIL. KM",
          time: "9 MONTHS",
        },
        {
          name: "EUROPA",
          description:
            "The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.",
          distance: "628 MIL. KM",
          time: "3 YEARS",
        },
        {
          name: "TITAN",
          description:
            "The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.",
          distance: "1.6 BIL. KM",
          time: "7 DAYS",
        },
      ],
      currentIndex: 0,
    };
  },
  mounted() {
    window.addEventListener("keydown", (e) => {
      const slide = e.code;
      if (slide === "ArrowRight") {
        if (this.locations.length - 1 <= this.currentIndex) {
          this.currentIndex = -1;
        }
        this.currentIndex++;
      }
      if (slide === "ArrowLeft") {
        if (this.currentIndex <= 0) {
          this.currentIndex = this.locations.length;
        }
        this.currentIndex--;
      }
    });
  },
  methods: {
    locationTo(clicked) {
      this.currentIndex = clicked;
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

.destination {
  background: url("../assets/destination/background-destination-mobile.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  min-height: 100vh;
  text-align: center;
  .destination-content {
    padding-top: 90px;
    padding-bottom: 60px;
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
    .locations {
      .location {
        .location-item-image {
          display: flex;
          align-items: center;
          justify-content: center;
        }
        .location-text {
          overflow: hidden;
          .location-nav-buttons {
            margin: auto;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            width: 63%;
            max-width: 260px;
            button {
              border: unset;
              background-color: unset;
              font-family: "Barlow Condensed", sans-serif;
              font-size: 14px;
              letter-spacing: 2.36px;
              color: rgba(208, 214, 249);
              padding-bottom: 10px;
              cursor: pointer;
              &:hover {
                transition: box-shadow 0.15s linear;
                box-shadow: inset 0 -3px rgb(151, 151, 151);
              }
            }
            .active {
              color: #fff;
              box-shadow: inset 0 -3px #fff;
              &:hover {
                box-shadow: inset 0 -3px #fff;
              }
            }
          }
        }
        .destinations-container {
          display: flex;
          align-items: center;
          justify-content: center;
          height: 450px;
          //   overflow: hidden;
          flex-basis: 50%;
        }
      }
    }
  }
  @include tablet {
    background: url("../assets/destination/background-destination-tablet.jpg");
    background-repeat: no-repeat;
    background-position: top center;
    background-size: cover;
    .destination-content {
      padding-top: 130px;
      padding-bottom: 40px;
      > p {
        text-align: start;
        padding-left: 40px;
        font-size: 20px;
        letter-spacing: 3.38px;
      }
      .locations {
        .location {
          .location-item-image {
            margin-bottom: 30px;
          }
          .location-text {
            .location-nav-buttons {
              margin-bottom: unset;
              max-width: 280px;
              button {
                font-size: 16px;
                letter-spacing: 2.7px;
              }
            }
          }
          .destinations-container {
            height: 390px;
          }
        }
      }
    }
  }
  @include desktop {
    background: url("../assets/destination/background-destination-desktop.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    text-align: unset;
    .destination-content {
      padding-top: 160px;
      padding-bottom: 30px;
      > p {
        text-align: start;
        padding-left: 11%;
        font-size: 28px;
        letter-spacing: 4.72px;
        margin-bottom: 50px;
      }
      .locations {
        .location {
          width: 90%;
          margin: auto;
          display: flex;
          align-items: center;
          justify-content: center;
          .location-item-image {
            margin-bottom: unset;
            padding-right: 50px;
            flex-basis: 42%;
          }
          .location-text {
            flex-basis: 50%;
            max-width: 445px;
            .location-nav-buttons {
              margin: unset;
              margin-bottom: 20px;
              max-width: 280px;
              button {
                font-size: 16px;
                letter-spacing: 2.7px;
              }
            }
            .destinations-container {
              flex-basis: 50%;
            }
          }
        }
      }
    }
  }
}
</style>
