<template>
    <form @submit="onSubmit" class="add-form">
      <div class="form-control">
        <label>Task</label>
        <input v-model="text" type="text" name="text" placeholder="Add Task" />
      </div>
      <div class="form-control">
        <label>Day & Time</label>
        <input
          v-model="day"
          type="text"
          name="day"
          placeholder="Add Day & Time"
        />
      </div>
      <div class="form-control form-control-check">
        <label>Set Reminder</label>
        <input v-model="reminder" type="checkbox" name="reminder" />
      </div>
      <input type="submit" value="Save Task" class="btn-block" />
    </form>
  </template>
  
  <script>
  export default {
    name: "MyTask",
    data() {
      return {
        text: "",
        day: "",
        reminder: "",
      };
    },
    methods: {
      onSubmit(e) {
        e.preventDefault();
  
        if (!this.text) {
          alert("Please Add A Task");
          return;
        }
  
        const newTask = {
          // id: Math.floor(Math.random() * 100000),
          text: this.text,
          day: this.day,
          reminder: this.reminder,
        };
  
        this.$emit("add-task", newTask);
  
        this.text = "";
        this.day = "";
        this.reminder = "";
      },
    },
  };
  </script>
  
  <style scoped>
  .btn-block {
    background-color: black;
    width: 100%;
    border: none;
    color: white;
    font-family: inherit;
    padding: 10px 0;
    border-radius: 5px;
    display: block;
    cursor: pointer;
  }
  
  .add-form {
    margin-bottom: 40px;
  }
  
  .form-control {
    margin: 20px 0;
  }
  
  .form-control label {
    display: block;
  }
  
  .form-control input {
    width: 100%;
    border-radius: 7px;
    height: 40px;
    margin: 5px;
    border: none;
    padding: 3px 8px;
    font-size: 17px;
  }
  
  .form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  .form-control-check label {
    flex: 1;
  }
  
  .form-control-check input {
    flex: 2;
    height: 20px;
  }
  </style>