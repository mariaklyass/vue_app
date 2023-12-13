<template>
  <div class="post">
    <div class="posts">
      <div>
        <strong>{{ post.setup }} ... </strong>
      </div>
      <div>... {{ post.punchline }}</div>
    </div>

    <div class="post__btns">
      <!-- <button><img src="../../public/edit.svg" /></button> -->
      <button @click="$emit('remove', post)">
        <img src="../../public/close.svg" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.post {
  display: flex;
  justify-content: space-between;
  align-items: self-start;
  border: 1px solid teal;
  border-radius: 0.5rem;
  margin: 1rem;
  padding: 1rem;
}
.posts {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1.5rem;
}
.post__btns {
  display: flex;
}
.post__btns img {
  width: 20px;
  height: 20px;
}
.post__btns button {
  background-color: transparent;
}
</style>
