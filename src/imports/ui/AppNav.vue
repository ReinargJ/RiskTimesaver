<template>
  <nav>
    <div class="app-title">Risk Timesaver</div>
    <router-link :to="{ name: 'home' }" exact>Home</router-link>
  </nav>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  methods: {
  },
}
</script>

<style lang="less" scoped>
@import "style/imports";

nav {
  background: @app-color;
  display: flex;
  flex-direction: row;
  align-items: center;
  color: white;
  padding-top: 24px;

  > * {
    flex: 0 0 auto;
  }

  a {
    color: white;
    display: inline-block;
    padding: 16px 28px;
    border-radius: 3px 3px 0 0;

    &:hover {
      background: lighten(@app-color, 10%);
    }

    &.router-link-active {
      background: @page-background;
      color: @app-color;
    }
  }
}

.app-title {
  font-size: 1.3rem;
  padding: 0 18px;
}

.actions {
  flex: 1 1 auto;
  text-align: right;
  padding: 4px 12px;
}

</style>
