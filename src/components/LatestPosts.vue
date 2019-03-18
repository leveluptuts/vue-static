<template>
  <section>
    <h3>Latest Posts</h3>
    <article v-for="edge in $static.allBlogPost.edges" :key="edge.node.id">
      <div v-html="edge.node.content"/>
      <h4>{{edge.node.title}}</h4>
      <p>{{edge.node.date}}</p>
      <g-link :to="`/posts/${edge.node.slug}`">Read More</g-link>
    </article>
  </section>
</template>

<static-query>
  query LatestPosts {
    allBlogPost (perPage: 2) {
      edges {
        node {
          id
          title
          tags
          slug
          date (format: "MMM Do YYYY")
        }
      }
    }
  }
</static-query>