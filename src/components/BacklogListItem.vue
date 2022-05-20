<template>
  <li class="backlog-list__item" v-for="post in posts" :key="post">
    <div class="post">{{ post.value }}</div>
  </li>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped>
.backlog-list__item {
  display: flex;
  justify-content: space-between;
  gap: 32px;
}
.backlog-list__item {
  padding-bottom: 8px;
  border-bottom: 2px solid #d8d8d8;
}

.backlog-list__item:not(:first-child) {
  margin-top: 32px;
}
</style>