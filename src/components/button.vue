<template>
    <button class="btn" @click="handleClick">
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    methods: {
      handleClick() {
        this.$emit('click');
      }
    }
  };
  </script>
  
  <style scoped>
  .btn i{
    padding: 0 .5rem;
    font-size: 1.8rem;
}

.btn:hover{
    background: var(--yellow);
}
  </style>
  