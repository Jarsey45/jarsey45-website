
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
      .then(({ data }) => {
        this.projects = data;
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
}

#section {
  @media screen and (min-width: 1200px) {
    @include fontResize();
  }
  @media screen and (max-width: 1200px) {
    font-size: 0.6em;
  }

  flex: 8;
  height: 100%;

  overflow: hidden;
  overflow-y: scroll;

  #list {
    width: 100%;
    padding-top: 5%;
    padding-bottom: 2em;

    .card {
      @include fadeCard;
      position: relative;
      box-sizing: border-box;
      padding: 20px;
      width: 80%;
      margin-left: 10%;
      @media screen and (max-width: 1200px) {
        margin-left: 15%;
        font-size: 1.4em;
      }
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
        @media screen and (max-width: 1200px) {
          font-size: 1.5em;
        }
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
          background: $dark-color;
          color: $dark-font-color;
        }

        @media screen and (max-width: 1200px) {
          font-size: 0.9em;
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
        @media screen and (max-width: 1200px) {
          width: 2em;
          height: 2em;
        }
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
      @media screen and (max-width: 1200px) {
        display: none;
      }
    }
    .card:hover:before {
      left: 0;
    }
  }
}
</style>