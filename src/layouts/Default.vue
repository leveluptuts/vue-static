<template>
  <div>
    <header class="header">
      <strong>
        <g-link to="/">{{ $static.metaData.siteName }}</g-link>
      </strong>
      <nav class="nav">
        <g-link class="nav__link" to="/">Home</g-link>
        <g-link class="nav__link" to="/about">About</g-link>
        <g-link class="nav__link" to="/posts">Posts</g-link>
      </nav>
    </header>
    <g-image v-if="background" :src="background" class="billboard"/>
    <div class="layout">
      <transition name="fade" appear>
        <main>
          <slot/>
        </main>
      </transition>
      <LatestPosts/>
    </div>
  </div>
</template>

<script>
import LatestPosts from "~/components/LatestPosts.vue";

export default {
  props: ["background"],
  components: {
    LatestPosts
  }
};
</script>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<style lang="scss">
body {
  font-family: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto,
    "Helvetica Neue", Arial, sans-serif;
  margin: 0;
  padding: 0;
  line-height: 1.5;
  font-size: $baseFontSize;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  max-width: 760px;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  padding: 20px;
  margin: 0 auto;
}

.billboard {
  width: 100%;
  height: auto;
}

.nav__link {
  margin-left: 20px;
}

.fade-enter-active {
  transition: 1s ease opacity;
}

.fade-enter {
  opacity: 0;
}
</style>
