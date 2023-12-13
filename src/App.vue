<script setup>
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <div>
    <img src="/vite.svg" class="logo" alt="Vite logo" />
    <img src="/vue.svg" class="logo vue" alt="Vue logo" />
  </div>

  <HelloWorld msg="Vite + Vue" />

  <div class="create-posts">
    <MyButton @click="fetchPosts" type="button">Загрузить</MyButton>
    <MyButton @click="showModal"> Создать </MyButton>
  </div>

  <MyModal v-model:show="modalVisible">
    <PostForm @create="createPost" />
  </MyModal>
  <PostList v-bind:posts="posts" @remove="removePost" />
  <!-- :posts  -->
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import MyButton from "./components/UI/MyButton.vue";
import MyModal from "./components/UI/MyModal.vue";
import axios from "axios";

export default {
  components: { PostForm, PostList },
  data() {
    return {
      posts: [],
      modalVisible: false,
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.modalVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showModal() {
      this.modalVisible = true;
    },
    async fetchPosts() {
      try {
        const response = await axios.get(
          "https://official-joke-api.appspot.com/jokes/programming/ten"
        );
        this.posts = response.data;
      } catch (e) {
        alert("Упс, ашипка!");
      }
    },
  },
};
</script>

<style>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo.vue {
  height: 5.5em;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.create-posts {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  margin-bottom: 2rem;
}
</style>
