<template>
  <span class="edit">
    <span v-if="isEdit">
      <input @blur="changeTitle" type="text" v-model="newTitle"/>
    </span>
    <span v-else @dblclick="isEdit = true">
      {{ todo.title | uppercase }}
    </span>
  </span>
</template>

<script>
import Vue from "vue";
Vue.filter("uppercase", function (value) {
  return value.toUpperCase();
});
export default {
  data() {
    return {
      newTitle: "",
      isEdit: false,
    };
  },
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  methods: {
    changeTitle() {
      if (this.newTitle) {
        this.$emit("change-title", this.todo.id, this.newTitle);
        this.newTitle = ""
      }
      this.isEdit = false;
    },
  },
};
</script>

<style scoped>
.edit {
  margin-left: 1rem;
}
</style>
