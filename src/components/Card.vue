//TODO: Accent for every project, from db; 
<template>
  <div class="card">
    <div class="nav-box">
      <div>
        <div class="link" @click="toLink">Preview!</div>
      </div>
      <div class="title">{{ title }}</div>
      <div>
        <img
          class="github"
          src="../assets/github64.png"
          @click="toGithub"
          alt="github"
        />
      </div>
    </div>
    <div class="divider"></div>
    <div class="description">
      {{ desc }}
    </div>
    <div class="lang-box">
      <div class="lang-left">Used languages</div>
      <div class="lang-right">
        <span v-for="(l, index) of lang" :key="index"> {{ l }}</span>
      </div>
    </div>
    <div class="date">Uploaded {{ date }}</div>
  </div>
</template>

<script>
export default {
  props: ["title", "desc", "lang", "link", "github", "date"],
  data() {
    return {};
  },
  methods: {
    toGithub() {
      window.location.href = this.github;
    },
    toLink() {
      window.location.href = this.link;
    },
  },
};
</script>

<style>
</style>