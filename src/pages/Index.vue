<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <div v-for="post in $page.allPost.edges" :key="post.node.path" class="post-list">
      <h2><router-link :to="post.node.path"> {{ post.node.title }} </router-link></h2>
      <h4>{{ moment(post.node.date).format('MMMM d, YYYY') }}</h4>
      <p>{{ post.node.summary }}</p>
    </div>

  </Layout>
</template>

<page-query>
  query {
    allPost {
      edges {
        node {
          path
          title
          date
          summary
        }
      }
    }
  }
</page-query>
<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
.post-list {
  border: 2px solid #ccc;
  border-radius: 10px;
  margin-bottom: 10px;
  padding: 10px;
}

.post-list h2, .post-list h2 a {
  margin: 0;
  color: #27ae60;
  text-decoration: none;
}

.post-list h4 {
  margin: 0;
  color: #aaa;
}
</style>
