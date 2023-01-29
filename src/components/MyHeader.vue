<template>
    <header>
      <h1>{{ title }}</h1>
      <Button
        @btn-click="$emit('toggle-add-task')"
        :text="showAddTask ? 'Close' : 'Add Task'"
        :color="showAddTask ? 'Red' : 'Green'"
      />
    </header>
  </template>
  
  <script>
  import Button from "./MyButton";
  
  export default {
    name: "MyHeader",
    props: {
      title: String,
      showAddTask: Boolean,
    },
    components: {
      Button,
    },
  };
  </script>
  
  <style scoped>
  header {
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
  </style>