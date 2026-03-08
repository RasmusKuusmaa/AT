<template>
  <div class="job-list">
    <h1>Applied positions</h1>
    <button class="add-btn" @click="showAddModal = true">+</button>
    <div 
        v-for="job in jobs"
        :key="job.id"
        :class="['job-card', job.status.toLowerCase()]"
        @click="openDescription(job)"
      >
      <h2> {{job.company}} - {{job.role}}</h2>
      <p>{{job.url}}</p>
      <p>{{job.status}}</p>
      <p>{{job.dateApplied}}</p>
  </div>
</div>

<div v-if="showAddModal" class="modal-overlay">
  <div class="Addmodal">
    <h2>Add new Application</h2>

    <h4>Company</h4>
    <input v-model="newJob.company" placeholder="Company">
    <h4>Role</h4>
    <input v-model="newJob.role" placeholder="role">

    <div class="modal-actions">
      <button @click="addjob">Save</button>
      <button @click="showAddModal = false">Cancel</button>
    </div>
  </div>

</div>

<div v-if="showDescriptionModal" class="modal-overlay">
  <div class="descriptionModal" @click.stop>
    <h2>{{selectedJob?.company}} - {{selectedJob?.role}}</h2>

    <p><strong>Status: </strong>{{selectedJob?.status}}</p>
    <p><strong>Date Applied: </strong>{{selectedJob?.dateApplied}}</p>
    <p><strong>URL: </strong>{{selectedJob?.url}}</p>
    
    <p><strong>Description:</strong></P>
    <p>{{selectedJob?.description}}</p>

    <p><strong>Stack:</strong></p>
    <ul>
      <li v-for="tech in selectedJob?.stack" :key="tech">
        {{tech}}
      </li>
    </ul>

    <button @click="showDescriptionModal = false">Close</button>
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

.add-btn {
  width: 2rem;
  height: 2rem;
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 1rem;
  border: none;
  border-radius: 6px;
  background-color: gray;
  color: black;
  cursor: pointer;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.6);
  display: flex;
  justify-content: center;
  align-items: center;
}

.Addmodal {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  width: 300px;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.descriptionModal {
  background: white;
  padding: 2rem;
  border-radius: 8px; 
  width: 400;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  }
</style>

<script setup lang="ts">
import {ref} from 'vue';

const showAddModal = ref(false);
const showDescriptionModal = ref(false);
const selectedJob = ref(null);

const openDescription = (job) => {
  selectedJob.value = job;
  showDescriptionModal.value = true;
}

const newJob = ref({
  company: '',
  role: '',
  url: '',
  status: '',
  dateApplied: '',
  description: '',
  stack: []
})

const addjob = () => {
  jobs.value.push({
    id: Date.now(),
    ...newJob.value
  })

  newJob.value = {
    company: '',
    role: '',
    url: '',
    status: '',
    dateApplied: '',
    description: '',
    stack: [],
  }

  showAddModal.value = false;
}

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
