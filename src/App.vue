<template>
  <div>
    <button @click="toggleLayout">{{ layoutButton }}</button>
    <div v-if="isListLayout" class="post-list">
      <div v-for="(post, index) in posts" :key="index">
        <h3>{{ post.content }}</h3>
        <p>By {{ post.user }} on {{ post.date_created }}</p>
      </div>
    </div>
    <div v-else class="post-grid">
      <div v-for="(post, index) in posts" :key="index">
        <div class="post-card">
          <h3>{{ post.content }}</h3>
          <p>By {{ post.user }} on {{ post.date_created }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        { content: "Post 1 content", user: "User 1", date_created: "2022-01-01" },
        { content: "Post 2 content", user: "User 2", date_created: "2022-02-01" },
        { content: "Post 3 content", user: "User 3", date_created: "2022-03-01" },
      ],
      isListLayout: true
    }
  },
  computed: {
    layoutButton() {
      return this.isListLayout ? 'Grid' : 'List'
    }
  },
  methods: {
    toggleLayout() {
      this.isListLayout = !this.isListLayout
    }
  }
}
</script>

<style>
.post-list {
  display: flex;
  flex-direction: column;
}
.post-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
.post-card {
  border: 1px solid gray;
  padding: 10px;
}
</style>
