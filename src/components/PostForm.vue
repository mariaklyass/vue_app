<template>
  <form @submit.prevent class="create-post">
    <input
      v-model="post.setup"
      type="text"
      placeholder="Придумай шутку"
      class="input"
    />
    <input
      v-model="post.punchline"
      type="text"
      placeholder="...а здесь панч"
      class="input"
    />
  </form>
  <MyButton type="button" @click="createPost">Создать</MyButton>
</template>

<script>
import MyButton from "./UI/MyButton.vue";
export default {
  components: {
    MyButton,
  },
  data() {
    return {
      post: {
        setup: "",
        punchline: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        setup: "",
        punchline: "",
      };
    },
  },
};
</script>

<style scoped>
.load-post {
  display: flex;
  justify-content: center;
}
.create-post {
  display: flex;
  gap: 1rem;
  margin: 2rem;
}
.input {
  padding: 0 10px;
  width: 100%;
  height: 50px;
  border-radius: 0.5rem;
  text-align: center;
}
.input::placeholder {
  display: flex;
  flex-wrap: wrap;
}
</style>

<!--  LONG version
   v-bind:value="post.body"
      @input="body = $event.target.value"
     
    SHORT version
    v-model="post.body"
    -->
