<template>
  <Layout>
    <!-- Page Header -->
    <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="site-heading">
              <h1># {{ $page.tags.title }}</h1>
              <span class="subheading">A Blog Theme by Start Bootstrap</span>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div class="post-preview" v-for="post in $page.tags.posts" :key="post.id">
            <g-link :to="'/post/' + post.id">
              <h2 class="post-title">
                {{ post.title }}
              </h2>
              <!-- <h3 class="post-subtitle">
                Problems look mighty small from 150 miles up
              </h3> -->
            </g-link>
            <p class="post-meta">Posted by
              <a href="#">{{ post.author }}</a>
              on {{ post.created_at }}</p>
            <!-- <p>
              <span v-for="tag in edge.node.tags" :key="tag.id">
                <g-link :to="'/tag/' + tag.id">{{ tag.title }}</g-link>
                &nbsp;&nbsp;
              </span>
            </p> -->
          </div>
          <hr>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
  query($id: ID!) {
    tags: strapiTag(id: $id) {
      id,
      title,
      posts {
        id,
        title,
        author,
        created_at
      }
    }
  }
</page-query>
<script>
export default {
  name: 'TagPage'
}
</script>

<style>

</style>