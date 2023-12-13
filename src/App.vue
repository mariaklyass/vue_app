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
  <PostList v-bind:posts="posts" @remove="removePost" v-if="!isLoading" />
  <div v-else class="spinner-box">
    <div class="circle-border">
      <div class="circle-core"></div>
    </div>
  </div>
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
      isLoading: false,
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
        this.isLoading = true;
        setTimeout(async () => {
          const response = await axios.get(
            "https://official-joke-api.appspot.com/jokes/programming/ten"
          );
          this.posts = response.data;
          this.isLoading = false;
        }, 700);
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

@keyframes spin {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(359deg);
  }
}
.spinner-box {
  margin: auto;
  width: 300px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: transparent;
}
.circle-border {
  width: 150px;
  height: 150px;
  padding: 3px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  background: rgb(63, 249, 220);
  background: linear-gradient(
    0deg,
    rgba(61, 250, 222, 0.102) 33%,
    rgba(63, 249, 220, 1) 100%
  );
  animation: spin 0.8s linear 0s infinite;
}

.circle-core {
  width: 100%;
  height: 100%;
  background-color: #242424;
  border-radius: 50%;
}
</style>
