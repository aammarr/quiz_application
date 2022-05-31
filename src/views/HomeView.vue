<script setup>
import Start from "@/components/Start.vue";
import Quiz from "@/components/Quiz.vue";
import { ref } from "vue";
const showQuiz = ref(false);
</script>

<template>
  <main>
    <div>
      <Start @startQuiz="showQuiz = true" />
      <Quiz v-if="showQuiz" />
    </div>
  </main>
</template>
