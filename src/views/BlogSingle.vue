<template>
  <section class="py-5 text-center container">
    <div class="row py-lg-5">
      <div class="col-lg-6 col-md-8 mx-auto">
        <h1 class="fw-light">{{ post.title }}</h1>
        <div>
          <svg
            class="bd-placeholder-img card-img-top"
            width="100%"
            height="225"
            xmlns="http://www.w3.org/2000/svg"
            role="img"
            aria-label="Placeholder: {{ post.title }}"
            preserveAspectRatio="xMidYMid slice"
            focusable="false"
          >
            <title>{{ post.title }}</title>
            <rect width="100%" height="100%" fill="#55595c" />
            <text x="50%" y="50%" fill="#eceeef" dy=".3em">
              {{ post.title }}
            </text>
          </svg>
        </div>
        <p class="lead text-muted">{{ post.body }}.</p>
        <p>
          <a href="#" class="btn btn-primary my-2">Main call to action</a>
          <a href="#" class="btn btn-secondary my-2">Secondary action</a>
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Blog",
  mounted: function () {
    console.log("Blog Single Mounted!");
    this.axios.get(this.api).then((response) => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  data: function () {
    return {
      name: "My Blog Single",
      api:
        "https://jsonplaceholder.typicode.com/posts/" + this.$route.params.id,
      // "https://jsonplaceholder.typicode.com/posts/1",
      // "https://jsonplaceholder.typicode.com/posts/2",
      // "https://jsonplaceholder.typicode.com/posts/3",
      post: {
        title: "My Post",
        body: "lorem",
      },
    };
  },
};
</script>
