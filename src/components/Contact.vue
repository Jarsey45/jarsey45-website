<template>
  <div id="section">
    <div class="item">
      <img src="../assets/email.svg" class="icon" />
      <span :style="{ paddingTop: '0.3em' }">
        bkowalczyk.kontakt@gmail.com
      </span>
    </div>
    <div class="item">
      <img src="../assets/github64.png" class="icon" />
      <a href="https://github.com/Jarsey45">https://github.com/Jarsey45</a>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
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

  animation: fade 2s forwards;
}

#section {
  @include fadeCard();
  @media screen and (max-width: 1200px) {
    font-size: 0.2em;
  }

  flex: 8;
  //height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;

  .icon {
    width: 1em;
    height: 1em;
    padding-right: 1em;
  }
  .item {
    @media screen and (max-width: 1200px) {
      font-size: 3vw;
      text-align: center;
      padding: 0;
    }
    display: flex;
    padding: 0.5em;
    align-items: center;
    font-size: 3em;
    width: 60%;
    margin: 0 auto;
    transition: all 0.5s ease;

    a {
      text-decoration: none;
      color: $default-font-color;
      padding-top: 0.1em;

      &:hover {
        color: $primary-color;
        font-weight: 600;
      }
    }
  }
}
</style>