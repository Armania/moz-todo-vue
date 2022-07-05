<template>
  <form @submit.prevent="onSubmit">
      <h2 class="label-wrapper">
        <label for="new-todo-input" class="label__lg">
          What else you need "To Do"?
        </label>
      </h2>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off"
      v-model.lazy.trim="label"
    />
    <button type="submit" class="btn btn__primary btn__lg">+Add</button>
  </form>
</template>

<script>
  export default {
   methods: {
    onSubmit() {
      if(this.label === "") {
        return;
      }
      this.$emit('todo-added', this.label);
      console.log('Label value: ', this.label);
      this.label = "";
    }
   },
   data(){
    return {
      label: ""
    }
   }
};
</script>