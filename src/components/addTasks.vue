<template>
  <div class="add-task">
    <div class="add-task__body">
      <div class="add-task__header">
        <h2 class="add-task-header__item">Add a task</h2>
        <div class="add-task-header__close">
          <i class="material-icons add-task-header-close__item" @click="closePopup"> close </i>
        </div>
      </div>
      <div class="line"></div>
      <form class="form" v-on:submit.prevent>
        <input
            type="text"
            class="add-task__input"
            placeholder="Enter a new task"
            v-model="inputValue"
        />
        <input
            type="submit"
            class="add-task__submit"
            value="Add"
            @click="clickSubmit"
        >
      </form>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      inputValue: ""
    }
  },
  methods: {
    closePopup() {
      this.$emit('closePopup')
    },
    clickSubmit(event) {
      event.preventDefault();
     if(this.inputValue !== "") {
       this.$emit('clickSubmit', this.inputValue);
       this.inputValue = ""
       this.closePopup();
     } else {
       alert("Enter a task in the field!")
     }
    }
  }
}
</script>

<style scoped>
.add-task {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  background: rgba(255, 255, 255, 0.4);
  backdrop-filter: blur(10px);
  z-index: 10;
}

.add-task__body {
  position: relative;
  width: 30%;
  height: 300px;
  max-width: 1200px;
  background: #5b75e3;
  margin-top: 65px;
  margin-right: 1px;
  border-radius: 8px;
  padding: 32px;
  z-index: 2;
}

.add-task__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.add-task-header__item {
  color: #fff;
  padding-bottom: 8px;
  text-align: center;
}

.line {
  width: 100%;
  height: 1px;
  border-radius: 50%;
  background: #fff;
}

.form {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  margin-top: 64px;
}

.add-task__input {
  width: 80%;
  height: 40px;
  padding: 0 1rem;
  border: none;
  border-radius: 4px;
  font-size: 16px;
}

.add-task__submit {
  width: 200px;
  height: 40px;
  border-radius: 8px;
  border: none;
  text-align: center;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
}

.add-task-header__close {
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.add-task-header-close__item {
  color: #fff;
}



@media screen and (max-width: 1200px) {
  .add-task__body {
    width: 80%;
  }
}

@media screen and (max-width: 600px) {
  .add-task__body {
    width: 80%;
  }
  .form {
    display: block;
  }
  .add-task__input {
    width: 100%;
    margin-bottom: 16px;
  }
  .add-task__submit {
    width: 100%;
  }
}

@media screen and (max-width: 500px) {
  .add-task__body {
    width: 95%;
  }
}
</style>