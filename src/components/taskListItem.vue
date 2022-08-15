<template>
  <div
      class="task-list-item"
      v-for="post in posts"
      :key="post.id"
      :class="classTaskListItem"
  >
    <button class="item__radio" @click="$emit('markAsDone', post)"/>
    <div class="item__title" :class="{ completed: post.completed }">
      {{ post.title }}
      <div class="delete" @click="$emit('remove', post)"></div>
    </div>
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
      // completed: "inProcess"
    }
  }
}
</script>

<style scoped>
.task-list-item {
  position: relative;
  display: flex;
  padding-bottom: 16px;
  padding-left: 8px;
  padding-right: 0;
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
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512' width='30px' height='30px'%3E%3Cpath fill='%235b75e3' d='M504.1,256C504.1,119,393,7.9,256,7.9C119,7.9,7.9,119,7.9,256C7.9,393,119,504.1,256,504.1C393,504.1,504.1,393,504.1,256z'/%3E%3Cpath fill='%23FFF' d='M392.6,172.9c-5.8-15.1-17.7-12.7-30.6-10.1c-7.7,1.6-42,11.6-96.1,68.8c-22.5,23.7-37.3,42.6-47.1,57c-6-7.3-12.8-15.2-20-22.3C176.7,244.2,152,229,151,228.4c-10.3-6.3-23.8-3.1-30.2,7.3c-6.3,10.3-3.1,23.8,7.2,30.2c0.2,0.1,21.4,13.2,39.6,31.5c18.6,18.6,35.5,43.8,35.7,44.1c4.1,6.2,11,9.8,18.3,9.8c1.2,0,2.5-0.1,3.8-0.3c8.6-1.5,15.4-7.9,17.5-16.3c0.1-0.2,8.8-24.3,54.7-72.7c37-39.1,61.7-51.5,70.3-54.9c0.1,0,0.1,0,0.3,0c0,0,0.3-0.1,0.8-0.4c1.5-0.6,2.3-0.8,2.3-0.8c-0.4,0.1-0.6,0.1-0.6,0.1l0-0.1c4-1.7,11.4-4.9,11.5-5C393.3,196.1,397,184.1,392.6,172.9z'/%3E%3C/svg%3E") no-repeat center;
  border: none;
  margin-right: 12px;
  cursor: pointer;
}

.delete {
  width: 30px;
  height: 30px;
  background: url("data:image/svg+xml,%3Csvg fill='%235b75e3' xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' width='24px' height='24px'%3E%3Cpath d='M 10 2 L 9 3 L 3 3 L 3 5 L 4.109375 5 L 5.8925781 20.255859 L 5.8925781 20.263672 C 6.023602 21.250335 6.8803207 22 7.875 22 L 16.123047 22 C 17.117726 22 17.974445 21.250322 18.105469 20.263672 L 18.107422 20.255859 L 19.890625 5 L 21 5 L 21 3 L 15 3 L 14 2 L 10 2 z M 6.125 5 L 17.875 5 L 16.123047 20 L 7.875 20 L 6.125 5 z'/%3E%3C/svg%3E") no-repeat center;  cursor: pointer;
}

.item__title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.item__title.completed {
  text-decoration: line-through;
}

@media screen and (max-width: 600px) {
  .item__title {
    font-size: 18px;
  }
}

@media screen and (max-width: 500px) {
  .item__title {
    font-size: 16px;
  }
  .item__radio {
    width: 24px;
    height: 24px;
    margin-right: 16px;
  }
  .delete {
    width: 24px;
    height: 24px;
  }
}
</style>