<template>
    <div class="card">
        <p>{{ gameNumber }}</p>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  
  export default defineComponent({
    name: 'Card',
    props: {
        gameNumber: {
      type: Number,
      required: true,
    }
    },
  });
  </script>
  
  <style scoped>
  .card {
    background: gray;
    border-radius: 20px;
    padding: 1rem;
  }
  </style>
  