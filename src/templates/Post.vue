<template>
    <Layout>
        <header>
            <h1> {{ $page.post.title }} </h1>
            <h3 class="subheader"> 
                {{ moment($page.post.date).format('MMMM d, YYYY') }} 
                    &middot;
                {{ $page.post.timeToRead }} min. read 
                
            </h3> 
        </header>
        <div v-html="$page.post.content" class="post__content"/>
        <div class="tags">
            <span v-for="tag in $page.post.tags" :key="tag">
                {{ tag }}
            </span>
        </div>
    </Layout>
</template>

<page-query>
    query Post ($path: String!) {
        post (path: $path) {
            title,
            path,
            date,
            summary,
            tags,
            content,
            timeToRead
        }
    }
</page-query>

<script>
export default {
  metaInfo() {
      return {
          title: this.$page.post.title
      }
  }
}
</script>

<style>
    header .subheader {
        font-size: 1em;
        color: #AAAAAA;
    }
    .post__content {
        line-height: 200%;
    }

    .tags > span {
        background-color: #ddd;
        border-radius: 5px;
        padding: 5px;
        margin-right: 5px;
    }
</style>