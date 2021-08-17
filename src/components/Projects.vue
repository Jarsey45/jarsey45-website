
<template>
  <div id="section">
    <div id="list">
      <Card
        v-for="(p, index) of projects"
        :key="index"
        :title="p.name"
        :desc="p.desc"
        :link="p.link"
        :lang="p.lang"
        :date="p.date"
        :github="p.github"
      />
    </div>
  </div>
</template>

<script>
/* eslint-disable vue/no-unused-components */
import Card from "./Card.vue";

export default {
  data() {
    return {
      projects: [],
    };
  },
  mounted() {
    fetch("https://api.jarsey45.cloud/v1/projects")
      .then((resp) => resp.json())
      .then(({ projects }) => {
        this.projects = projects;
      });
  },
  methods: {},
  components: {
    Card,
  },
};
</script>

<style lang="scss" >
@use "../App" as *;

@mixin fadeCard {
  @keyframes fade {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  animation: fade 1s forwards;

  // @for $i from 1 to 2 {
  //   &:nth-child(#{$i}) {
  //     animation-delay: #{$i * 1s};
  //   }
  // }
}

#section {
  flex: 8;
  height: 100%;
  @include fontResize;

  #list {
    width: 100%;
    padding-top: 5%;

    .card {
      @include fadeCard;
      position: relative;
      box-sizing: border-box;
      padding: 20px;
      width: 80%;
      margin-left: 10%;
      margin-bottom: 4em;
      height: auto;
      border: 1px solid $border-color;
      border-radius: 5px;
      overflow: hidden;

      .nav-box {
        display: flex;
        width: 95%;
        margin: 0 auto;
      }

      .title {
        flex: 6;
        font-size: 2em;
        font-weight: 600;
        z-index: 1;
      }

      .divider {
        width: 95%;
        margin: 0 auto;
        border-top: 2px solid hsl(0, 0%, 65%);
      }

      .description {
        text-align: left;
        width: 80%;
        margin: 0 auto;
        margin-top: 10px;
      }

      .lang-box {
        display: flex;
        align-items: baseline;
        flex-wrap: wrap;
        width: 80%;
        margin: 0 auto;

        .lang-left {
          flex: 1;
          // padding: 1em;
          // margin-left: 4em;
          text-align: left;
          font-weight: 600;
        }

        .lang-right {
          flex: 7;
          display: flex;
          align-items: baseline;
          flex-wrap: wrap;

          span {
            text-align: center;
            margin-left: 2em;
            margin-top: 1em;
            background: $primary-color;
            padding: 0.5em;
            padding: 0.8em;
            color: $dark-font-color;
          }
        }
      }

      .link {
        cursor: pointer;
        flex: 1;
        font-weight: 600;
        padding: 0.3em;
        padding-top: 0.5em;
        transition: all 0.3s ease-in-out;
        font-size: 1em;
        //background: #000;

        &:hover {
          background: #000;
          color: $dark-font-color;
        }
      }

      .date {
        margin-top: 1em;
        font-size: 0.8em;
        color: hsl(0, 0%, 80%);
      }

      .github {
        box-sizing: content-box;
        cursor: pointer;
        flex: 1;
        width: 2.5em;
        height: 2.5em;
      }
    }

    .card:before {
      position: absolute;
      content: "";
      height: 100%;
      width: 3em;
      background: $primary-color;
      transform: skewX(30deg);
      top: 0;
      left: -50%;
      opacity: 0.8;
      transition: left 0.5s ease-in-out;
    }
    .card:hover:before {
      left: 0;
    }
  }
}
</style>