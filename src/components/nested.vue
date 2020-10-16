<template>
  <draggable :list="tasks" :group="{ name: 'g1' }" class="list-group">
      <b-list-group-item v-for="el in tasks" :key="el.name">
        <p>{{el.name}}</p>
        <nested-draggable :tasks="el.tasks" />
      </b-list-group-item>
   </draggable>
</template>
<script>
import draggable from "vuedraggable";
export default {
  props: {
    tasks: {
      required: true,
      type: Array
    }
  },
  components: {
    draggable
  },
  name: "nested-draggable"
};
</script>
<style scoped></style>
