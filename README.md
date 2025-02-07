# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

Learn more about IDE Support for Vue in the [Vue Docs Scaling up Guide](https://vuejs.org/guide/scaling-up/tooling.html#ide-support).
# Weather App

This is a simple Vue.js-based weather application that fetches real-time weather information using the OpenWeatherMap API. The app allows users to search for any city and view its current weather conditions, including temperature and weather descriptions.

---

## Features

- Search for weather by city name.
- Displays:
  - City name
  - Weather condition
  - Temperature in Celsius
- Responsive and user-friendly design.

---

## Tech Stack

- **Vue.js 3**: Frontend framework.
- **Axios**: For making HTTP requests.
- **OpenWeatherMap API**: For fetching weather data.
- **Vite**: Development server.
- **CSS**: For styling.

---

## Prerequisites

- Node.js and npm installed on your system.
- OpenWeatherMap API key (create a free account [here](https://home.openweathermap.org/users/sign_up)).

---

## Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/RahimjonovBoburjon/weather-app.git
   cd weather-app
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create an `.env` file in the root directory and add your OpenWeatherMap API key:
   ```env
   VITE_OPENWEATHERMAP_API_KEY=your_actual_api_key
   ```

4. Start the development server:
   ```bash
   npm run dev
   ```

5. Open the app in your browser:
   ```
   http://localhost:5173
   ```

---

## Project Structure

```
weather-app/
├── public/
├── src/
│   ├── assets/        # Images and static assets
│   ├── components/    # Vue components (if added)
│   ├── App.vue        # Main Vue file
│   ├── main.js        # Entry point for the app
│   └── styles.css     # Global styles
├── .env               # Environment variables
├── package.json       # Project configuration
├── vite.config.js     # Vite configuration
└── README.md          # Project documentation
```

---

## How to Use

1. Type a city name in the input field.
2. Press "Enter" or click the "Search" button.
3. The app will display the weather details for the entered city.

---

## Known Issues

- Ensure the API key is valid; otherwise, a `401 Unauthorized` error will occur.
- Network issues may lead to failed requests.

---

## Future Improvements

- Add a loading spinner while fetching data.
- Show additional weather details (humidity, wind speed, etc.).
- Implement a dark mode toggle.
- Allow users to search by coordinates or ZIP code.

---

## License

This project is licensed under the MIT License.

---

## Credits

- **OpenWeatherMap API**: [https://openweathermap.org/](https://openweathermap.org/)
- **Vue.js Documentation**: [https://vuejs.org/](https://vuejs.org/)

---

Feel free to contribute or raise issues on the [GitHub repository](https://github.com/RahimjonovBoburjon/weather-app).