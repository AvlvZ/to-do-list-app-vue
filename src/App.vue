<template>
  <div id="app">
    <div class="container">
      <div class="tasks">
        <taskHeader @clickSubmit="clickSubmit"/>
        <div class="task-list">
          <div class="country-post">Задач: {{posts.length}}</div>
          <taskListItem
              :posts="posts"
              @remove="removePost"
          />
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
        title: data
      }

      this.posts.push(newPosts)

      console.log(count);
      console.log(data)
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@200;300;400;500;600;700;800&display=swap');
* {
  font-family: 'Manrope', sans-serif;
  font-size: 20px;
  color: #636369;
  text-align: left;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #5b75e3;
}

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
</style>
