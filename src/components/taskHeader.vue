<template>
  <div class="tasks__header">
    <div class="task-header__body">
      <h1 class="header__date">
        {{ timeShaping }}
      </h1>
      <button @click="showPopup" class="new-task__btn">+</button>
    </div>
    <addTasks
        v-if="popupVisible"
        @closePopup="closePopup"
        @clickSubmit="clickSubmit"
    />
  </div>
</template>

<script>
import AddTasks from "@/components/addTasks";
import {format} from "date-fns";

export default {
  components: {AddTasks},
  data() {
    return {
      popupVisible: false,
    }
  },
  methods: {
    showPopup() {
      this.popupVisible = true;
    },
    closePopup() {
      this.popupVisible = false;
    },
    clickSubmit(data) {
      this.$emit('clickSubmit', data)
    }
  },
  computed: {
    timeShaping() {
      const dateFormat = format(new Date(), "eeee/dd/MMMM");
      return dateFormat.replaceAll("/", " ");
    }
  }
}
</script>

<style scoped>
.task-header__body {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 32px;
}

.new-task__btn {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  border: none;
  background: #5b75e3;
  color: #FFF;
  font-size: 32px;
  cursor: pointer;
}

.header__date {
  font-size: 28px;
}

@media screen and (max-width: 600px) {
  .header__date {
    font-size: 25px;
  }
}

@media screen and (max-width: 500px) {
  .header__date {
    font-size: 20px;
  }
}
</style>