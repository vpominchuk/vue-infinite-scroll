<script>
import { defineComponent } from "vue";
import InfiniteScroll from "@/vue-infinite-scroll.vue";

export default defineComponent({
  name: "ServeDev",
  components: {
    InfiniteScroll
  },

  data() {
    return {
      limit: 10,
      page: 0,

      posts: []
    }
  },

  methods: {
    async load() {
      this.page++

      try {
        const response = await fetch(
            'https://jsonplaceholder.typicode.com/posts?_limit=' + this.limit + '&_page=' + this.page
        );

        this.posts = [...this.posts, ...await response.json()];
        this.totalPages = Math.ceil(response.headers.get('x-total-count') / this.limit);
      } catch (e) {
        console.log(e);
      }
    }
  }
});
</script>

<template>
  <div id="app">
    <div class="posts">
      <div class="post" v-for="post in posts">
        <div class="title">{{ post.id }}: {{ post.title }}</div>
        <div class="body">{{ post.body }}</div>
      </div>
    </div>
    <infinite-scroll :active="this.page < this.totalPages" distance="50px" auto-load="true" @process="load" />
  </div>
</template>

<style scoped>
  .post {
    border: 2px solid #424242;
    margin-bottom: 20px;
  }

  .title {
    font-weight: bold;
  }
</style>