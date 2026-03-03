<template>
  <div class="job-list">
    <h1>Applied positions</h1>
    <div 
        v-for="job in jobs"
        :key="job.id"
        :class="['job-card', job.status.toLowerCase()]"
      >
      <h2> {{job.company}} - {{job.role}}</h2>
      <p>{{job.url}}</p>
      <p>{{job.status}}</p>
      <p>{{job.dateApplied}}</p>
  </div>
</div>
</template>

<style scoped>
  .job-list {
    width: 20rem;
    margin: 0 auto;
    padding: 1rem;

  }
  
  .job-card{
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 1rem;
    margin-bottom: 1rem;
    box-shadow: 0 2px 5px rgba(0,0,0,0.7);
     transition: transform 0.1s ease-in-out;
  }

  .job-card:hover {
    transform: scale(1.01) translateY(-0.4rem) translateX(0.4rem);
    cursor: pointer;
  }

.job-card.applied {
  background-color: yellow;
}

.job-card.interview {
  background-color: lightgreen;
}

.job-card.offer {
  background-color: green;
}

.job-card.rejected {
  background-color: red;
}
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
    status: "REJECTED",
    dateApplied: "2026-03-03",
    description: "eee i dunno",
    stack: ["python", "vue.js"]
  },
    {id: 3,
    company: "Micdrosoft",
    role: "juniour engineer",
    url: "youtube.com",
    status: "Offer",
    dateApplied: "2026-03-03",
    description: "eee i dunno",
    stack: ["python", "vue.js"]
  },
    {id: 4,
    company: "Micdrosoft",
    role: "juniour engineer",
    url: "youtube.com",
    status: "interview",
    dateApplied: "2026-03-03",
    description: "eee i dunno",
    stack: ["python", "vue.js"]
  }
])
</script>
