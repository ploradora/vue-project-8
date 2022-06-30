<template>
  <div class="destination">
    <div class="destination-content">
      <p><span>01</span> PICK YOUR DESTINATION</p>
      <div class="locations">
        <div class="location">
          <div class="location-image">
            <img src="../assets/destination/image-moon.png" alt="" />
          </div>
          <div class="location-text">
            <div class="location-nav-buttons">
              <button class="active" @click="locationTo('moon')">MOON</button>
              <button @click="locationTo('mars')">MARS</button>
              <button @click="locationTo('europa')">EUROPA</button>
              <button @click="locationTo('titan')">TITAN</button>
            </div>
            <h2 class="name">MOON</h2>
            <p class="description">
              See our planet as you’ve never seen it before. A perfect relaxing
              trip away to help regain perspective and come back refreshed.
              While you’re there, take in some history by visiting the Luna 2
              and Apollo 11 landing sites.
            </p>
            <div class="info">
              <div class="distance-container">
                <p class="info-header">AVG. DISTANCE</p>
                <p class="distance">384,400 KM</p>
              </div>
              <div class="duration-container">
                <p class="info-header">EST. TRAVEL TIME</p>
                <p class="duration">3 DAYS</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      locations: [
        {
          img: require("../assets/destination/image-moon.png"),
          alt: "the moon",
          name: "MOON",
          description:
            "See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.",
          distance: "384,400 KM",
          time: "3 DAYS",
        },
        {
          img: require("../assets/destination/image-mars.png"),
          alt: "mars",
          name: "MARS",
          description:
            "Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!",
          distance: "225 MIL. KM",
          time: "9 MONTHS",
        },
        {
          img: require("../assets/destination/image-europa.png"),
          alt: "europa moon",
          name: "EUROPA",
          description:
            "The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.",
          distance: "628 MIL. KM",
          time: "3 YEARS",
        },
        {
          img: require("../assets/destination/image-titan.png"),
          alt: "titan moon",
          name: "TITAN",
          description:
            "The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.",
          distance: "1.6 BIL. KM",
          time: "7 DAYS",
        },
      ],
      currentLocation: "moon",
    };
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
        .location-image {
          margin-top: 35px;
          margin-bottom: 35px;
          width: 100%;
          img {
            width: 50%;
          }
        }
        .location-text {
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
              padding-bottom: 20px;
            }
            .active {
              color: #fff;
              box-shadow: inset 0 -3px #fff;
            }
          }
          .name {
            font-family: "Bellefair", serif;
            font-weight: 100;
            font-size: 56px;
            color: #fff;
          }
          .description {
            width: 85%;
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
        }
      }
    }
  }
  @include tablet {
    background: url("../assets/destination/background-destination-tablet.jpg");
    background-repeat: no-repeat;
    background-position: top center;
    background-size: cover;
  }
  @include desktop {
    background: url("../assets/destination/background-destination-desktop.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
  }
}
</style>
