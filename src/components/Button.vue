<template>
  <button @click="createPopUp()" class="button_create">
    <span>{{ description }}</span>
  </button>
</template>

<script>
export default {
  props: {
    description: String,
    action: String,
  },
  methods: {
    createPopUp() {
      console.log("clicked");
    },
  },
};
</script>

<style>
.button_create {
  width: 289px;
  height: 47px;
  border: 5px solid #86cb92;
  border-radius: 10px;
  background-color: #71b48d;

  display: flex;
  justify-content: center;
  align-items: center;

  font-size: 1.1em;
  color: #eee;
  font-weight: bold;
}
</style>
