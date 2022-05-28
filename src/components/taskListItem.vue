<template>
  <div class="task-list-item"
       v-for="post in posts"
       :key="post.id"
       :class="classTaskListItem"
  >
    <button
        class="item__radio"
        @click="$emit('remove', post)"
    />
    <div class="item__title">{{post.title}}</div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  data() {
    return {
      classTaskListItem: "task-list-item__open",
      completed: "inProcess"
    }
  }
}
</script>

<style scoped>
.task-list-item {
  position: relative;
  display: grid;
  grid-template-columns: 30px 1fr 30px;
  gap: 16px;
  padding-bottom: 16px;
  padding-left: 8px;
  padding-right: 8px;
}
.task-list-item:not(:last-child) {
  margin-bottom: 16px;
}
.task-list-item::before {
  content: "";
  position: absolute;
  bottom: 0;
  left: 46px;
  width: calc(100% - 46px);
  height: 2px;
  background: #8a8a8a;
  transition: all .5s linear;
}
.item__radio {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: none;
  cursor: pointer;
}
.inProcess {
  background: url("https://i.ibb.co/28ssTcJ/Ellipse-1.png") center no-repeat;
  background-size: cover;
}
.completed {
  background: url("https://i.ibb.co/rdK0ctY/Vector.png") center no-repeat;
  background-size: 20px;
}
.item__title {
  display: flex;
  align-items: center;
}
.task-list-item__close::before {
  content: "";
  bottom: 60%;
  transform: translateY(-60%);
}
</style>