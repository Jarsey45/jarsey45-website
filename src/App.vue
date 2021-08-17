<template>
  <div id="flexbox">
    <Navbar @changeComponent="changeComp" />
    <Projects v-if="chosenComp === 'Projects'" />
    <About v-if="chosenComp === 'About'" />
    <Contact v-if="chosenComp === 'Contact'" />
  </div>
</template>

<script>
import "material-design-icons";
import Navbar from "./components/Navbar.vue";
import Projects from "./components/Projects.vue";
import About from "./components/About.vue";
import Contact from "./components/Contact.vue";

export default {
  name: "App",
  components: {
    Navbar,
    Projects,
    About,
    Contact,
  },
  computed: {},
  data() {
    return {
      chosenComp: "Projects",
    };
  },
  methods: {
    changeComp(name) {
      this.chosenComp = name;
    },
  },
};
</script>

<style lang="scss">
@use "./App" as *;

#app {
  width: 100%;
  height: 100%;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $default-font-color;
}

#flexbox {
  width: 100%;
  height: 100%;
  display: flex;
}
</style>
