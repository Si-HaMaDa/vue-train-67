<template>
  <section class="py-5 text-center container">
    <div class="row py-lg-5">
      <div class="col-lg-6 col-md-8 mx-auto">
        <h1 class="fw-light">{{ name }}</h1>
        <p class="lead text-muted">
          Something short and leading about the collection below—its contents,
          the creator, etc. Make it short and sweet, but not too short so folks
          don’t simply skip over it entirely.
        </p>
        <p>
          <a href="#" class="btn btn-primary my-2">Main call to action</a>
          <a href="#" class="btn btn-secondary my-2">Secondary action</a>
        </p>
      </div>
    </div>
  </section>
  <main>
    <div class="album py-5 bg-light">
      <div class="container">
        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
          <mainPost :posts="posts" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import mainPost from "../components/blog/mainPost.vue";
export default {
  name: "Blog",
  components: {
    mainPost,
  },
  mounted: function () {
    console.log("Blog Mounted!");
    this.axios.get(this.api).then((response) => {
      console.log(response.data);
      this.posts = response.data;
    });
  },
  data: () => {
    return {
      name: "My Blog",
      api: "https://jsonplaceholder.typicode.com/posts",
      posts: [],
    };
  },
};
</script>
