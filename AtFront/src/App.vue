<template>
  <div>
    <h1>Applied positions</h1>
    <div 
      v-for="job in jobs"
      :key="job.id"
      >
      <h2> {{job.company}} - {{job.role}}</h2>
      <p>{{job.url}}</p>
      <p>{{job.status}}</p>
      <p>{{job.dateApplied}}</p>
  </div>
</div>
</template>

<style scoped>

</style>

<script setup lang="ts">
import {ref} from 'vue';

const jobs = ref([
  {id: 1,
    company: "Microsoft",
    role: "juniour engineer",
    url: "youtube.com",
    status: "Applied",
    dateApplied: "2026-03-03",
    description: "eee i dunno",
    stack: ["python", "vue.js"]
  },
  {id: 2,
    company: "Micdrosoft",
    role: "juniour engineer",
    url: "youtube.com",
    status: "Applied",
    dateApplied: "2026-03-03",
    description: "eee i dunno",
    stack: ["python", "vue.js"]
  }
])
</script>