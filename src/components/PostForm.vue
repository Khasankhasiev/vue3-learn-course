<template>
  <div>
    <form @submit.prevent>
      <h4>Создание поста</h4>
      <my-input
        v-focus
        v-model="post.title"
        type="text"
        placeholder="Название поста"
      />
      <my-input v-model="post.body" type="text" placeholder="Описание поста" />
      <my-button
        @click="createPost"
        style="align-self: flex-end; margin-top: 15px"
        >Создать</my-button
      >
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      if (this.post.title.trim() !== "" && this.post.body.trim() !== "") {
        this.post.id = Date.now();
        this.$emit("create", this.post);
        this.post = {
          title: "",
          body: "",
        };
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
