<template>
  <div v-show="posts.length > 0">
    <PostItem
      class="post"
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @remove="$emit('remove', post)"
    ></PostItem>
  </div>
  <div v-show="posts.length === 0">
    <div class="post example">
      <div><strong>Шутка: </strong>тратаата?...</div>
      <div><strong>Продолжение: </strong>...ляляляля!</div>
    </div>
    <h4>
      Тут пока ничего нет. <br />Нажми на кнопку "Загрузить"/"Создать",<br />
      чтобы заполнить пространство!
    </h4>
  </div>
</template>

<script>
import PostItem from "./PostItem.vue";

export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  components: { PostItem },
};
</script>

<style scoped>
.post {
  border: 1px solid teal;
  border-radius: 0.5rem;
  margin: 1rem;
  padding: 1rem;
}
.example {
  position: relative;
}
.example::after {
  content: "Я просто пример";
  display: block;
  position: absolute;
  top: -15px;
  font-style: italic;
  padding: 0 10px;
  background-color: #242424;
}
</style>
