<template>
  <div id="app">
    <div class="container">
      <div class="tasks">
        <taskHeader @clickSubmit="clickSubmit" />
        <div class="task-list">
          <div class="country-post">Tasks: {{ getTotalCount }}</div>
          <taskListItem :posts="posts" @markAsDone="markAsDone" @remove="removePost"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import TaskHeader from "@/components/taskHeader";
import TaskListItem from "@/components/taskListItem";

export default {
  components: {TaskListItem, TaskHeader},
  data() {
    return {
      posts: []
    }
  },
  methods: {
    clickSubmit(data) {
      const count = this.posts.length
      const newPosts = {
        id: count + 1,
        title: data,
        completed: false
      }
      this.posts.push(newPosts);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    markAsDone(post) {
      const newPost = {...post};
      newPost.completed = !newPost.completed;
      this.posts = this.posts.map((p) => (p.id === post.id ? newPost : p));
    },
  },
  computed: {
    getTotalCount() {
      return this.posts.filter((p) => !p.completed).length;
    }
  },
}
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  max-width: 1920px;
  margin: 0 auto;
  overflow: hidden;
}

.container {
  width: 100%;
}

.tasks {
  width: 50%;
  height: 100%;
  max-width: 1200px;
  background: #FFF;
  padding: 32px;
  border-radius: 8px;
  margin: 32px auto;
}
.country-post {
  font-size: 22px;
  font-weight: 700;
  color: #5b75e3;
  margin-top: 16px;
  margin-bottom: 32px;
}

@media screen and (max-width: 1200px) {
  .tasks {
    width: 80%;
  }
}

@media screen and (max-width: 600px) {
  .tasks {
    width: 80%;
  }
  .country-post {
    font-size: 18px;
  }
}

@media screen and (max-width: 500px) {
  .tasks {
    width: 95%;
  }
  .country-post {
    font-size: 16px;
  }
}
</style>
