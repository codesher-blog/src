<template>
  <header>
    <div class="title">
      <img class="logo" src="../assets/logo.svg"/>
      <div class="text">
        <h2><router-link class="app-link" to="/posts" target="_self"> {{title}} </router-link></h2>
        <p>{{description}}</p>
      </div>
    </div>
    <div class="buttons">
      <a class="button app-link" href="/oauth/1" target="_self" v-if="!$store.state.accessToken">ورود</a>
      <a class="button app-link" target="_self" v-else @click="$store.dispatch('clearAccessToken')">خروج</a>
    </div>
  </header>
</template>

<script>
import { getConfig } from "../utils/index.js";

export default {
  data() {
    return {
      title: getConfig().title,
      description: getConfig().description
    };
  }
};
</script>

<style lang="scss" scoped>
@import "../styles/functions";

header {
  color: $color;
  height: auto;
  overflow: auto;
  padding: 25px 0;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;

  & > .title {
    padding: 0 15px;
    height: auto;
    overflow: auto;
    display: flex;
    flex-direction: row;
    align-items: center;

    & > .text {
      line-height: 1.5;

      & > h2 {
        font-size: 3em;
        font-weight: bold;
      }
    }

    & > img.logo {
      width: 120px;
    }
  }

  & > .buttons {
    padding: 0 15px;

    & > .button {
      font-size: 1.4em;
      margin-right: 3px;
      cursor: pointer;
    }
  }

  @media (min-width: 768px) {
    width: 768px;
    margin: 0 auto;
  }
  @media (max-width: 767px) {
    & > .title > .text > p {
      display: none;
    }
  }
}
</style>

