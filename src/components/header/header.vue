<script>
import { mapActions } from 'vuex';

const ENTER_KEY = 'Enter';

export default {
  data: () => ({
    name: ''
  }),
  methods: {
    handleChange(event) {
      this.name = event.target.value;
    },
    handleSubmit(event) {
      if (event.key !== ENTER_KEY) {
        return;
      }

      this.onCreate(this.name);
      this.name = '';
    },
    ...mapActions(['onCreate'])
  }
};
</script>
<template>
  <header class="header">
    <span class="header-span"><img class="header-img" src="../../../images/Logo_cropped_medium.png" /></span>
    <p class="header">Enter a list of items below</p>
    <input
      class="new-todo"
      placeholder="What do we need to buy?"
      :value="name"
      @input="handleChange"
      @keyup="handleSubmit"
    />
  </header>
</template>
