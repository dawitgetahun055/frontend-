<template>
  <input type="checkbox" />
  <label for="">{{ task.task }}</label>
</template>

<script>
export default {
  props: ["task"],
};
</script>

<style scoped>
label {
  font-size: 20px;
  margin-left: 15px;
}

input[type="checkbox"] {
  width: 20px;
  height: 20px;
}
</style>
