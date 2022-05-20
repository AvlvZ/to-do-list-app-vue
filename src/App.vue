<template>
  <div id="app">
    <h1>To Do Application</h1>
    <hr>
    <div class="backlogs">
      <ul class="backlog__list">
        <BacklogListItem :posts="posts"/>
      </ul>
    </div>
    <form class="add-backlog">
      <input v-bind:value="inputValue" @input="createInput" type="text" class="add-backlog__input" placeholder="Добавить задачу">
      <input @click="addBacklog" type="button" class="add-backlog__submit" value="Добавить">
    </form>
  </div>
</template>

<script>

import BacklogListItem from "@/components/BacklogListItem";
export default {
  components: {BacklogListItem},
  data() {
    return {
      posts: [

      ],
      inputValue: ""
    }
  },
  methods: {
    addBacklog() {
      const newPost = {
        id: Date.now(),
        value: this.inputValue
      };
      this.posts.push(newPost);
      this.inputValue = "";
    },
    createInput(event) {
      this.inputValue = event.target.value;
    }
  }
}
</script>

<style>
* {
  text-align: left;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #d8d8d8;
}

#app {
  width: 100%;
  max-width: 1920px;
  margin: 0 auto;
  overflow: hidden;
}

h1 {
  text-align: center;
  margin: 32px 0;
}

.backlogs {
  width: 50%;
  height: 500px;
  max-width: 1200px;
  background: #FFF;
  padding: 32px;
  border-radius: 8px;
  margin: 32px auto;
  overflow-y: scroll;
}

.backlog__list {
  list-style: none;
}

.add-backlog {
  display: flex;
  gap: 5%;
  width: 50%;
  height: 40px;
  max-width: 1200px;
  border-radius: 16px;
  margin: 32px auto;
}

.add-backlog__input {
  width: 100%;
  height: 100%;
  padding: 0 2rem;
  border: 2px solid #a4a4a4;
}

.add-backlog__submit {
  padding: 0 2rem;
  border: 2px solid #a4a4a4;
  background: #FFF;
  cursor: pointer;
}
</style>
