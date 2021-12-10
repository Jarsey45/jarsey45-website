<template>
  <div id="section">
    <div id="card">
      <div id="title">
        I'm <span class="highlight"> Bartłomiej </span>
        <p>
          I'm
          <span class="highlight">{{ new Date().getYear() - 101 }} </span> years
          old coding enthusiast.
        </p>
        <p>
          I started my journey with
          <span class="highlight">C++</span>, after a while I found out about
          <span class="highlight">JavaScript</span>,
          <span class="highlight">NodeJS</span> and
          <span class="highlight">ReactJS</span>.
          <b> I quickly fell for them. </b>
        </p>
        <p>
          Now I write mostly in <span class="highlight">Vue</span> and
          <span class="highlight">ReactJS</span> with some addons. <br /><b
            >Though I'm constantly learning :)</b
          >
        </p>
      </div>
      <div id="options">
        <div
          class="opt"
          :class="{ active: this.active[0] }"
          @click="changeOpt(0)"
        >
          <span>Skills</span>
        </div>
        <div
          class="opt"
          :class="{ active: this.active[1] }"
          @click="changeOpt(1)"
        >
          Education
        </div>
        <div
          class="opt"
          :class="{ active: this.active[2] }"
          @click="changeOpt(2)"
        >
          Interests
        </div>
      </div>

      <div v-if="active[0]" id="list">
        <div id="flexbox">
          <div
            v-for="(skill, index) of skills"
            :key="index"
            :class="skill.prof"
          >
            {{ skill.name }}
          </div>
        </div>
      </div>

      <div v-if="active[1]" id="list">
        <ul>
          <li v-for="(e, index) of edu" :key="index" class="list-item">
            <span v-if="e === currEdu" style="color: #41b883; font-weight: 600">
              {{ e }}
            </span>
            <span v-else>{{ e }}</span>
          </li>
        </ul>
      </div>

      <div v-if="active[2]" id="list">
        <ul>
          <li v-for="(i, index) of interests" :key="index" class="list-item">
            {{ i }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      skills: [
        {
          name: "JavaScript",
          prof: "high",
        },
        {
          name: "ReactJS",
          prof: "high",
        },
        {
          name: "React Native",
          prof: "medium",
        },
        {
          name: "Redux",
          prof: "medium",
        },
        {
          name: "Vue.js",
          prof: "low",
        },
        {
          name: "NodeJS",
          prof: "medium",
        },
        {
          name: "TypeScript",
          prof: "medium",
        },
        {
          name: "SASS/LESS",
          prof: "medium",
        },
      ],
      edu: [
        "ZSŁ W KRAKOWIE,  UPPER - SECONDARY SCHOOLS OF COMMUNICATIONS",
        "Politechnika Krakowska",
        "...?",
      ],
      currEdu: "Politechnika Krakowska",
      interests: [
        "Coding :)",
        "Learning new stuff",
        "Listening to music, especially Lo-Fi",
        "Movies and series",
        "Running",
      ],
      active: [true, false, false],
    };
  },
  methods: {
    changeOpt(id) {
      const newActive = [false, false, false];
      newActive[id] = !newActive[id];
      this.active = newActive;
    },
  },
};
</script>

<style lang="scss" >
@use "../App" as *;

@keyframes moveHigh {
  from {
    background: #eaeaea;
  }
  to {
    background: $high-color;
  }
}

@keyframes moveMedium {
  from {
    background: #eaeaea;
  }
  to {
    background: $medium-color;
  }
}

@keyframes moveLow {
  from {
    background: #eaeaea;
  }
  to {
    background: $low-color;
  }
}

@keyframes fadeText {
  from {
    color: #eaeaea;
  }
  to {
    color: $default-font-color;
  }
}

@mixin fadeCard($duration) {
  @keyframes fade {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  animation: fade $duration forwards;
}

@mixin makeKeyframe($keyframeName) {
  animation: $keyframeName 2s;
  animation-fill-mode: forwards;
}

#section {
  flex: 8;
  height: 100%;

  #card {
    box-sizing: border-box;
    @include fadeCard(1s);

    //border: 1px solid hsl(0, 0, 80%); //to Delete
    width: 80%;
    height: 70%;
    margin: 6em auto;

    #title {
      font-size: 3em;

      p {
        text-align: left;
        font-size: 0.5em;
        padding: 0 3em;
        color: hsl(0, 1%, 70%);
      }
    }

    #options {
      @include fadeCard(3s);

      height: 1.6em;
      display: flex;
      width: 80%;
      margin: 0 auto;
      font-weight: 600;
      font-size: 1.2em;

      .opt {
        cursor: pointer;
        box-sizing: content-box;

        margin-right: 2em;
        padding: 0.5em 0.4em;
        border-radius: 5px 5px 0px 0px;
        text-decoration: underline;
        text-decoration-style: line;
        text-decoration-thickness: 2px;
        transition: all 0.3s cubic-bezier(0, 0, 0.23, 1);

        &:hover,
        &.active {
          color: $tertiary-color;
          // color: $primary-color;
          background: #eaeaea;
          font-size: 1.1em;
        }
      }
    }

    #list {
      width: 85%;
      height: auto;
      margin: 0 auto;
      border-radius: 5px;
      background: #eaeaea;
      padding-bottom: 4em;
      transition: all 0.5s ease-in-out;

      #flexbox {
        margin: auto auto;
        display: flex;
        align-items: baseline;
        flex-wrap: wrap;
        width: 95%;

        div {
          text-align: center;
          margin-left: 2em;
          margin-top: 1em;
          padding: 0.5em;
          padding-top: 0.8em;
          color: $dark-font-color;
        }

        .high {
          @include makeKeyframe("moveHigh");
        }
        .medium {
          @include makeKeyframe("moveMedium");
        }
        .low {
          @include makeKeyframe("moveLow");
        }
      }

      .list-item {
        width: 85%;
        margin: 0 auto;
        padding: 0.2em;
        font-size: 1.8em;
        text-align: left;

        @include makeKeyframe("fadeText");
      }
    }
  }
}

.highlight {
  color: $primary-color;
}
</style>