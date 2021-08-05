<template>
  <div class="task">
    <div class="description">
      <h4>{{ task.desc }}</h4>
      <p>{{ task.day }}</p>
    </div>
    <button
      @click="doTask(task.id)"
      :class="[task.done ? 'checked' : 'check']"
    ></button>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    doTask(id) {
      this.$emit("do-task", id);
    },
  },
};
</script>
<style>
.task {
  border: 6px solid #86cb92;
  width: 28em;
  height: 5em;

  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: space-between;
  padding-top: 1em;
  padding-left: 1em;

  background-color: #71b48d;
  border-radius: 10px;

  margin-top: 1.5em;
}

.task .description h4 {
  color: #ffffff;
  font-weight: bold;
  font-size: 15px;
}

.task .description p {
  color: #eeeeee;
  font-size: 12px;
}

.task .check {
  width: 2em;
  height: 2em;
  border-radius: 50%;
  background-color: #86cb92;
  border: 3px solid #eeeeee;

  margin-top: 5px;
  margin-right: 10px;
}

.task .checked {
  width: 2em;
  height: 2em;
  border-radius: 50%;
  background-color: #28587b;
  border: 3px solid #eeeeee;

  margin-top: 5px;
  margin-right: 10px;
}
</style>
