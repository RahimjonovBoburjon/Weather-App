<template>
  <div id="app">
    <div class="container">
      <h1>Ob-havo ilovasi</h1>
      <input v-model="city" @keyup.enter="getWeather" placeholder="Shahar nomini kiriting" class="input-field" />
      <button @click="getWeather" class="btn">Qidirish</button>

      <div v-if="weather" class="weather-info">
        <h2>{{ weather.name }} - {{ weather.weather[0].description }}</h2>
        <p>Harorat: {{ weather.main.temp }}°C</p>
      </div>

      <div v-if="error" class="error">
        <p>{{ error }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      city: '',
      weather: null,
      error: ''
    };
  },
  methods: {
    async getWeather() {
      if (!this.city) return;
      try {
        const apiKey = '03a456ea66848038444e4f141ba0441f';
        const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${apiKey}&units=metric`);
        this.weather = response.data;
        this.error = '';
      } catch (error) {
        this.error = 'Shahar topilmadi yoki xatolik yuz berdi!';
        this.weather = null;
        console.log(error);
      }
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Arial', sans-serif;
  background-color: #f4f4f9;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  text-align: center;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

h1 {
  margin-bottom: 20px;
  color: #333;
}

.input-field {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 70%;
  margin-bottom: 20px;
}

.btn {
  padding: 10px 20px;
  background-color: #007BFF;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
}

.btn:hover {
  background-color: #0056b3;
}

.weather-info {
  margin-top: 20px;
}

.error {
  margin-top: 20px;
  color: red;
}
</style>