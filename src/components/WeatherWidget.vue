<template>
  <div class="weather-widget">
    <h2>Widget Cuaca</h2>
    <div class="search-bar">
      <input v-model="city" placeholder="Enter city name" @keyup.enter="getWeather" />
      <button @click="getWeather">Search</button>
    </div>
    <div v-if="weather" class="weather-info">
      <div class="weather-item">
        <p><strong>Location:</strong> {{ weather.name }}</p>
        <img src="../assets/loc.png" alt="location icon" />
        <div class="weather-border"></div>
      </div>
      <div class="weather-item">
        <p><strong>Temperature:</strong> {{ weather.main.temp }}°C</p>
        <img src="../assets/temp.png" alt="temperature icon" />
        <div class="weather-border"></div>
      </div>
      <div class="weather-item">
        <p><strong>Weather:</strong> {{ weather.weather[0].description }} </p>
        <img :src="`http://openweathermap.org/img/wn/${weather.weather[0].icon}.png`" alt="weather icon" />
        <div class="weather-border"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const city = ref('')
const weather = ref(null)

const getWeather = async () => {
  const apiKey = 'b15e9858a62c81eadb4c772801a4aa29'
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city.value}&units=metric&appid=${apiKey}`

  try {
    const response = await axios.get(url)
    weather.value = response.data
  } catch (error) {
    console.error(error)
    weather.value = null
  }
}
</script>

<style scoped>
.weather-widget {
  padding: 20px;
  border: 1px solid #00bfff;
  border-radius: 10px;
  max-width: 750px;
  margin: 50px auto;
  text-align: center;
  background-color: whitesmoke;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.weather-widget h2 {
  color: #00bfff;
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 20px;
}

.search-bar {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.search-bar input {
  padding: 15px;
  width: 70%;
  margin-right: 10px;
  border: 1px solid #00bfff;
  border-radius: 5px;
  background-color: whitesmoke;
  color: black;
}

.search-bar button {
  padding: 10px;
  border: 1px solid #87CEFA;
  background-color: #00bfff;
  color: whitesmoke;
  cursor: pointer;
  border-radius: 5px;
}

.search-bar button:hover {
  background-color: #008ee6;
}

.weather-info {
  margin-top: 20px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.weather-item {
  margin: 10px;
  border: 1px solid #00bfff;
  border-radius: 5px;
  padding: 10px;
  flex: 1;
  background-color: whitesmoke;
  text-align: center;
  width: 200px;
}

.weather-item img {
  margin-top: 10px;
  width: 35px;
  height: 35px;
}

.weather-item p {
  margin: 0;
  color: #00bfff;
}

.weather-border {
  border-top: 1px solid #00bfff;
  margin-top: 10px;
  padding-top: 10px;
}
</style>
