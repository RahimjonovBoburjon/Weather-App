<template>
  <div id="app">
    <div class="container">
      <h1>Ob-havo ilovasi</h1>
      <input v-model="city" @keyup.enter="getWeather" placeholder="Shahar nomini kiriting" class="input-field" />
      <button @click="getWeather" class="btn">Qidirish</button>

      <div v-if="weather && weather.weather && weather.weather.length > 0" class="weather-info">
        <h2>{{ weather.name }} - {{ weather.weather[0].description }}</h2>
        <h4>Harorat: {{ weather.main.temp }}°C</h4>
      </div>

      <div v-if="error" class="error">
        <p>{{ error }}</p>
      </div>
      <h3 class="footer">Powered by <a href="https://github.com/RahimjonovBoburjon">Bobur</a></h3>
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
        const apiKey = import.meta.env.VITE_OPENWEATHERMAP_API_KEY;
        const response = await axios.get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${apiKey}&units=metric`
        );
        this.weather = response.data;
        this.error = '';
        this.city = '';
      } catch (error) {
        if (error.response && error.response.status === 404) {
          this.error = 'Shahar topilmadi!';
        } else {
          this.error = 'Xatolik yuz berdi: ' + error.message;
          console.log(apiKey);

        }
        this.weather = null;
        console.error(error);
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
  background-color: #b3b3b9;
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
  padding: 20px;
  border: 2px solid #007BFF;
  border-radius: 8px;
  background: linear-gradient(135deg, #dbeafe, #bfdbfe);
  color: #1e3a8a;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.weather-info h2 {
  font-size: 24px;
  margin-bottom: 10px;
  font-weight: bold;
  color: #1d4ed8;
}

.weather-info h4 {
  font-size: 18px;
  margin: 5px 0;
}

.error {
  margin-top: 20px;
  color: red;
  background-color: #ffe6e6;
  padding: 10px;
  border: 1px solid red;
  border-radius: 4px;
}

.footer {
  margin-top: 8px;
  color: #504e4e;
}
</style>