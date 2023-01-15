<template>
  <main>
    <welcame :posts="posts" />
    <div>
      <ul>
        <li v-if="posts" v-for="(post, index) in posts" :key="index">
          <span> {{ post.breed }} </span>
          <span> {{ post.country }} </span>
        </li>
      </ul>
    </div>
  </main>
</template>
<script>
export default {
  data() {
    return {
      posts: [],
    };
  },
  props: {
    posts: []
  },
  methods: {
    getPosts() {
      fetch("https://catfact.ninja/breeds")
        .then((response) => response.json())
        .then((data) => this.posts = data.data);
    },
  },
  created(){
    this.getPosts();
  }
};
</script>
