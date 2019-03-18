<template>
  <div>
    <h1>Layout TWO!</h1>
    <slot/>
    <LatestPosts v-if="latest"/>
  </div>
</template>

<script>
import LatestPosts from "../components/LatestPosts.vue";

export default {
  props: ["latest"],
  components: {
    LatestPosts
  }
};
</script>
