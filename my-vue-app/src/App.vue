<template>
  <div>
    <div class="todo">
      <img src="./assets/Pencil.svg" alt="" />
      <h1>To do list</h1>
    </div>
    <div class="list-container">
      <h1>Keep track of your tasks here!</h1>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <list-item :task="task"></list-item>
        </li>
      </ul>
    </div>
    <form @submit.prevent="addTask" class="input-container">
      <div>
        <input type="text" ref="taskInputRef" />
        <button>Add</button>
      </div>
    </form>
  </div>
</template>

<script>
import ListItem from "./components/ListItem.vue";
export default {
  components: { ListItem },
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      const enteredTask = this.$refs.taskInputRef.value;
      if (enteredTask === "") return;

      const newTask = {
        task: enteredTask,
        done: false,
      };

      this.tasks.push(newTask);
    },
  },
};
</script>

<style>
body {
  background-color: white;
  color: black;
  padding: 0;
  margin: 0;
}

img {
  width: 50px;
}

.todo {
  display: flex;
  gap: 20px;
  border-bottom: 1px solid gray;
  align-items: center;
  justify-content: center;
  height: 90px;
  width: 30%;
  position: absolute;
  top: 10%;
  left: 50%;
  transform: translateX(-50%);
}

img {
  width: 40px;
}

.list-container {
  position: relative;
  top: -20px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}

.list-container li {
  display: flex;
  align-items: center;
  border-bottom: 1px solid lightgray;
  margin-top: 10px;
}

.list-container li.checked {
  text-decoration: line-through;
}

.list-container h1 {
  font-size: 25px;
}

.list-container ul {
  list-style: none;
}

.input-container {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  top: 100px;
}

.input-container > div {
  display: flex;
  gap: 20px;
}

.input-container button:hover {
  background-color: lightslategray;
  outline: none;
  border: none;
}

.input-container input {
  width: 250px;
  height: 50px;
  border-radius: 15px;
  padding-inline: 20px;
  font-size: 20px;
}
</style>
