<!-- MyComponent.vue -->

<template>
  <div>
    <button @click="getRandomDataClick" class="styled-button">Get Random Data with Basic Authentication</button>
    <span> &nbsp;</span>
   <button  @click="getProjectHealthCheck" class="styled-button">Project Health Check Point</button> 
   <div>&nbsp;</div>
   <div class="grid-header"> <div v-if="healthCheck">Apllication Status: {{healthCheck.status}}</div> </div> 
  <div v-if="apiData" class="grid-container">
<div class="grid-header">Picture</div>
<div class="grid-header"> Name</div>
<div class="grid-header">Email</div>
<div class="grid-header">Gender</div>
<div class="grid-header">Address</div>
<div class="grid-header">Phone</div>
<div class="grid-header">Age</div>
   <div class="column">
    <img :src="apiData.picture.medium" alt="User Thumbnail" /></div>
    <div class="column"> {{ apiData.name.title }} {{apiData.name.first}} {{apiData.name.last}}</div>
      <div class="column">{{ apiData.email }}</div>
      <div class="column">{{ apiData.gender }}</div>
      <div class="column">{{ apiData.location.city }} {{ apiData.location.state }} {{ apiData.location.country}}
      {{ apiData.location.street.name }}, {{ apiData.location.street.number }}</div>
      <div class="column">{{ apiData.phone }}</div>
      <div class="column">{{ apiData.dob.age }}</div>
  </div>

    </div>
</template>


<style>
body {
    margin: 0;
    font-family: 'Arial', sans-serif;
}

.grid-container {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: auto;
    gap: 10px;
    padding: 10px;
}

.grid-header { 
    text-align: auto;
    font-weight: bold;
    background-color: #f0f0f0;
    padding: 10px;
    min-width:10%;
    box-sizing: border-box;
    border: 1px solid #ddd;
    text-align: center;
}

.column {
    text-align: center;
    font-weight: normal;
    background-color: #f0f0f0;
    padding: 10px;
    min-width:10%;
    box-sizing: border-box;
    padding: 10px;
    border: 1px solid #ddd;
    text-align: center;

}

.styled-button {
    padding: 10px 20px;
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    text-decoration: none;
    cursor: pointer;
    border: 2px solid #3498db;
    border-radius: 5px;
    color: #3498db;
    background-color: #ffffff;
    transition: background-color 0.3s ease, color 0.3s ease;
    /* Hover effect */
    &:hover {
        background-color: #3498db;
        color: #ffffff;
    }
    }
</style>

// MyComponent.vue

<script>

import axios from 'axios';
export default {
  name: 'User',
  data() {
    return {
      apiData: null,
      healthCheck: null

    };
  },
  methods: {

    async getRandomDataClick() {
        try {
          const response = await axios.get('http://0.0.0.0:8000/user', {
            headers: {
              Authorization: 'Basic ' + btoa('ashish:saxena'),
            }});
            this.apiData = response.data; 
        } catch (error) {
          console.error('Error making Randdom API call:', error);
        }
      },
      async getProjectHealthCheck() {
      try {
        const response = await axios.get('http://0.0.0.0:8000/health');
          this.healthCheck = response.data;
      } catch (error) {
        console.error('Error fetching project health check :', error);
      }
    },
  },
};
</script>
