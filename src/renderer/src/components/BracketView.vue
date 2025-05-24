<template>
  <div class="bracket-container">
    <h1 class="title">Bracket</h1>

    <div
      class="team-card"
      v-for="(team, index) in teams"
      :key="index"
    >

  
      <div class="field file-wrapper">
        <label>Team Image</label>
        <input
          class="custom-file"
          type="file"
          accept="image/*"
      
        />
       
        <img
          v-if="team.image"
          :src="team.image"
          alt="Team Image"
          class="preview"
        />
      </div>

     
      <div class="field file-wrapper">
        <label>Team Flag</label>
        <input
          class="custom-file"
          type="file"
          accept="image/*"
       
        />
      
        <img
          v-if="team.flag"
          :src="team.flag"
          alt="Team Flag"
          class="preview"
        />
      </div>

      <div class="field">
        <label>Team Name</label>
        <input
          type="text"
          v-model="team.name"
          placeholder="Enter team name"
        />
      </div>

      <div class="field">
        <label>Team Score</label>
        <input
          type="number"
          v-model.number="team.score"
          min="0"
          placeholder="0"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

const teams = reactive(
  Array.from({ length: 32 }, () => ({
    image: null,
    flag: null,
    name: '',
    score: 0,
  }))
)

</script>

<style scoped>
.bracket-container {
  padding: 2rem;
  background: #121826;
  color: #fff;
  min-height: 100vh;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.title {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  text-align: center;
}

.team-card {
  background: #1f2937;
  padding: 1rem;
  border-radius: 0.75rem;
  margin-bottom: 1rem;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  transition: transform 0.2s ease, ;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.team-card:hover {
  transform: scale(1.01);
  background: #273549;
}

.field {
  display: flex;
  flex-direction: column;
}

label {
  font-size: 0.9rem;
  margin-bottom: 0.25rem;
  color: #cbd5e1;
}

input[type="text"],
input[type="number"],
input[type="file"] {
  padding: 0.5rem;
  border: 1px solid #3b4252;
  background: #2e3440;
  color: #e5e9f0;
  border-radius: 6px;
  font-size: 0.95rem;
}

input[type="text"]:focus,
input[type="number"]:focus {
  outline: 2px solid #4f46e5;
}

.preview {
  margin-top: 0.5rem;
  max-height: 60px;
  object-fit: contain;
  border: 1px solid #444;
  border-radius: 6px;
}

.file-wrapper {
  position: relative;
}



.custom-file::file-selector-button {
 
  color: #22c55e;
  background: transparent;
  border: none;
  font-weight: bold;
  cursor: pointer;
}



</style>