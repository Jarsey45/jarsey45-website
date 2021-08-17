<template>
  <nav>
    <div id="name">
      <div id="box">
        Bartłomiej Kowalczyk
        <p>aka. Jarsey45</p>
      </div>
    </div>
    <div
      class="sub"
      @click="subClick(0, 'Projects')"
      :class="{ active: active[0] }"
    >
      Projects
    </div>
    <div
      class="sub"
      @click="subClick(1, 'About')"
      :class="{ active: active[1] }"
    >
      About
    </div>
    <div
      class="sub"
      @click="subClick(2, 'Contact')"
      :class="{ active: active[2] }"
    >
      Contact
    </div>
    
  </nav>
</template>

<script>
export default {
  data() {
    return {
      active: [true, false, false],
    };
  },
  methods: {
    subClick(id, name) {
      const newActive = [false, false, false];
      newActive[id] = !newActive[id];
      this.active = newActive;
      this.$emit("changeComponent", name);
    },
  },
};
</script>

<style lang="scss" >
@use "../App" as *;

nav {
  flex: 2;
  border-right: 1px solid $border-color;
  @include fontResize();

  #name {
    color: $primary-color;
    cursor: context-menu;
    font-weight: 600;
    font-size: 1.5em;
    padding: 1em;
    border-bottom: 1px solid $border-color;

    p {
      color: hsl(1, 0%, 80%);
      font-size: 0.5em;
    }
  }

  .sub {
    cursor: pointer;

    text-align: left;
    font-size: 1.2em;
    padding: 1em;
    padding-left: 2em;
    height: 1em;
    display: block;
    //overflow: hidden;

    background: linear-gradient(
      to right,
      $primary-color 50%,
      $background-color 50%
    );
    background-size: 200% 101%;
    background-position: right top;
    transition: all 0.5s ease-out;
    border: none;

    &:hover {
      background-position: left bottom;
      padding-left: 3em;
      color: $dark-font-color;
    }

    &.active {
      background: #010101;
      padding-left: 3em;
      color: $dark-font-color;
      transition: none;
    }
  }
}
</style>