# Repo
Code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App - FYP</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f0f8ff;
        }
        
        .weather-header {
            background-color: #0d6efd;
            color: white;
            padding: 20px 0;
            margin-bottom: 30px;
        }
        
        .weather-card {
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            background-color: white;
        }
        
        .current-weather {
            background-color: #0d6efd;
            color: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }
        
        .weather-icon {
            font-size: 60px;
            margin: 10px 0;
        }
        
        .forecast-day {
            text-align: center;
            padding: 15px;
            border-right: 1px solid #eee;
        }
        
        .forecast-day:last-child {
            border-right: none;
        }
        
        .search-box {
            margin-bottom: 30px;
        }
        
        .temperature {
            font-size: 48px;
            font-weight: bold;
        }
        
        .city-name {
            font-size: 24px;
        }
        
        .weather-detail {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .weather-detail i {
            width: 30px;
            color: #0d6efd;
            font-size: 18px;
        }
        
        footer {
            background-color: #333;
            color: white;
            padding: 20px 0;
            margin-top: 40px;
        }
        
        .popular-cities {
            cursor: pointer;
        }
        
        .popular-cities li:hover {
            background-color: #f8f9fa;
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#"><i class="fas fa-cloud-sun me-2"></i>Weather App</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link active" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#forecast">Forecast</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#about">About</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Header -->
    <header class="weather-header">
        <div class="container text-center">
            <h1>Weather Forecast</h1>
            <p class="lead">Get accurate weather updates for any location</p>
        </div>
    </header>

    <!-- Main Content -->
    <div class="container">
        <!-- Search Box -->
        <div class="row justify-content-center">
            <div class="col-md-6">
                <div class="search-box">
                    <div class="input-group">
                        <input type="text" class="form-control" id="cityInput" placeholder="Enter city name...">
                        <button class="btn btn-primary" id="searchBtn" type="button">
                            <i class="fas fa-search"></i> Search
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Weather Display -->
        <div class="row">
            <!-- Current Weather -->
            <div class="col-md-8">
                <div class="weather-card" id="currentWeather">
                    <div class="row">
                        <div class="col-md-6">
                            <div class="current-weather">
                                <div class="weather-icon">
                                    <i class="fas fa-sun" id="weatherIcon"></i>
                                </div>
                                <h2 class="temperature" id="temperature">32°C</h2>
                                <p id="weatherCondition">Sunny</p>
                                <h3 class="city-name" id="cityName">Karachi, Pakistan</h3>
                                <p id="dateTime">Monday, 5 May 2025 | 12:00 PM</p>
                            </div>
                        </div>
                        <div class="col-md-6">
                            <div class="p-4">
                                <h4 class="mb-4">Weather Details</h4>
                                <div class="weather-detail">
                                    <i class="fas fa-temperature-high"></i>
                                    <div>
                                        <p class="mb-0">Feels Like</p>
                                        <h6 id="feelsLike">34°C</h6>
                                    </div>
                                </div>
                                <div class="weather-detail">
                                    <i class="fas fa-tint"></i>
                                    <div>
                                        <p class="mb-0">Humidity</p>
                                        <h6 id="humidity">65%</h6>
                                    </div>
                                </div>
                                <div class="weather-detail">
                                    <i class="fas fa-wind"></i>
                                    <div>
                                        <p class="mb-0">Wind</p>
                                        <h6 id="wind">12 km/h</h6>
                                    </div>
                                </div>
                                <div class="weather-detail">
                                    <i class="fas fa-compress-alt"></i>
                                    <div>
                                        <p class="mb-0">Pressure</p>
                                        <h6 id="pressure">1012 hPa</h6>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- 5 Day Forecast -->
                <div class="weather-card p-3" id="forecast">
                    <h4 class="mb-3">5-Day Forecast</h4>
                    <div class="row" id="forecastContainer">
                        <div class="col forecast-day">
                            <div>Tue</div>
                            <i class="fas fa-sun"></i>
                            <div>32° / 25°</div>
                        </div>
                        <div class="col forecast-day">
                            <div>Wed</div>
                            <i class="fas fa-cloud-sun"></i>
                            <div>30° / 24°</div>
                        </div>
                        <div class="col forecast-day">
                            <div>Thu</div>
                            <i class="fas fa-cloud"></i>
                            <div>29° / 23°</div>
                        </div>
                        <div class="col forecast-day">
                            <div>Fri</div>
                            <i class="fas fa-cloud-rain"></i>
                            <div>27° / 22°</div>
                        </div>
                        <div class="col forecast-day">
                            <div>Sat</div>
                            <i class="fas fa-cloud-sun"></i>
                            <div>28° / 23°</div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Sidebar -->
            <div class="col-md-4">
                <!-- Popular Cities -->
                <div class="weather-card">
                    <div class="card-header bg-primary text-white">
                        <h5 class="mb-0">Popular Cities</h5>
                    </div>
                    <ul class="list-group list-group-flush popular-cities" id="popularCities">
                        <li class="list-group-item" data-city="Karachi">Karachi, Pakistan</li>
                        <li class="list-group-item" data-city="Lahore">Lahore, Pakistan</li>
                        <li class="list-group-item" data-city="Islamabad">Islamabad, Pakistan</li>
                        <li class="list-group-item" data-city="Peshawar">Peshawar, Pakistan</li>
                        <li class="list-group-item" data-city="Quetta">Quetta, Pakistan</li>
                    </ul>
                </div>

                <!-- Weather News -->
                <div class="weather-card mt-4">
                    <div class="card-header bg-success text-white">
                        <h5 class="mb-0">Weather News</h5>
                    </div>
                    <div class="card-body">
                        <div class="mb-3 pb-2 border-bottom">
                            <h6>Heat Wave Expected Next Week</h6>
                            <p class="small text-muted mb-0">Temperatures expected to rise significantly next week...</p>
                        </div>
                        <div class="mb-3 pb-2 border-bottom">
                            <h6>Monsoon Update: Above Average Rainfall</h6>
                            <p class="small text-muted mb-0">Meteorological Department predicts heavy rain...</p>
                        </div>
                        <div>
                            <h6>Air Quality Improves After Recent Rain</h6>
                            <p class="small text-muted mb-0">Air quality index shows improvement...</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- About Section -->
        <section id="about" class="my-5">
            <div class="weather-card p-4">
                <h2 class="mb-4">About This Project</h2>
                <p>This Weather App is a Final Year Project for Web Engineering. It demonstrates the implementation of various web technologies:</p>
                <ul>
                    <li>HTML5 for structure</li>
                    <li>CSS3 for styling</li>
                    <li>JavaScript for interactivity</li>
                    <li>Bootstrap for responsive design</li>
                    <li>React components for user interface elements</li>
                </ul>
                <p>The application provides real-time weather data, forecasts, and other weather-related information in a user-friendly interface.</p>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer class="text-center">
        <div class="container">
            <p>© 2025 Weather App | Final Year Project - Web Engineering</p>
            <div class="social-icons">
                <a href="#" class="text-white mx-2"><i class="fab fa-facebook"></i></a>
                <a href="#" class="text-white mx-2"><i class="fab fa-twitter"></i></a>
                <a href="#" class="text-white mx-2"><i class="fab fa-instagram"></i></a>
                <a href="#" class="text-white mx-2"><i class="fab fa-github"></i></a>
            </div>
        </div>
    </footer>

    <!-- JavaScript -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // Wait for the DOM to load
        document.addEventListener('DOMContentLoaded', function() {
            // Sample data for different cities
            const cityData = {
                'Karachi': {
                    temp: 32,
                    condition: 'Sunny',
                    icon: 'fa-sun',
                    feelsLike: 34,
                    humidity: 65,
                    wind: 12,
                    pressure: 1012
                },
                'Lahore': {
                    temp: 30,
                    condition: 'Partly Cloudy',
                    icon: 'fa-cloud-sun',
                    feelsLike: 32,
                    humidity: 68,
                    wind: 10,
                    pressure: 1014
                },
                'Islamabad': {
                    temp: 28,
                    condition: 'Cloudy',
                    icon: 'fa-cloud',
                    feelsLike: 29,
                    humidity: 72,
                    wind: 8,
                    pressure: 1015
                },
                'Peshawar': {
                    temp: 31,
                    condition: 'Clear',
                    icon: 'fa-sun',
                    feelsLike: 33,
                    humidity: 60,
                    wind: 14,
                    pressure: 1011
                },
                'Quetta': {
                    temp: 25,
                    condition: 'Rainy',
                    icon: 'fa-cloud-rain',
                    feelsLike: 26,
                    humidity: 75,
                    wind: 15,
                    pressure: 1009
                }
            };

            // Update weather based on city
            function updateWeather(city) {
                const data = cityData[city] || cityData['Karachi'];
                
                // Update DOM elements
                document.getElementById('cityName').textContent = city + ', Pakistan';
                document.getElementById('temperature').textContent = data.temp + '°C';
                document.getElementById('weatherCondition').textContent = data.condition;
                document.getElementById('feelsLike').textContent = data.feelsLike + '°C';
                document.getElementById('humidity').textContent = data.humidity + '%';
                document.getElementById('wind').textContent = data.wind + ' km/h';
                document.getElementById('pressure').textContent = data.pressure + ' hPa';
                
                // Update weather icon
                document.getElementById('weatherIcon').className = '';
                document.getElementById('weatherIcon').classList.add('fas', data.icon);
                
                // Update date and time
                const now = new Date();
                const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
                const timeString = now.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
                document.getElementById('dateTime').textContent = now.toLocaleDateString('en-US', options) + ' | ' + timeString;
            }

            // Initial weather update
            updateWeather('Karachi');
            
            // Search button click handler
            document.getElementById('searchBtn').addEventListener('click', function() {
                const city = document.getElementById('cityInput').value.trim();
                if (city) {
                    // Check if city exists in our data
                    if (cityData[city]) {
                        updateWeather(city);
                    } else {
                        // Add a new city with random data if it doesn't exist
                        cityData[city] = {
                            temp: Math.floor(Math.random() * 10) + 25,
                            condition: ['Sunny', 'Cloudy', 'Partly Cloudy', 'Rainy', 'Clear'][Math.floor(Math.random() * 5)],
                            icon: ['fa-sun', 'fa-cloud', 'fa-cloud-sun', 'fa-cloud-rain', 'fa-sun'][Math.floor(Math.random() * 5)],
                            feelsLike: Math.floor(Math.random() * 10) + 25,
                            humidity: Math.floor(Math.random() * 30) + 50,
                            wind: Math.floor(Math.random() * 10) + 5,
                            pressure: Math.floor(Math.random() * 10) + 1005
                        };
                        updateWeather(city);
                    }
                    // Clear input
                    document.getElementById('cityInput').value = '';
                }
            });
            
            // Handle enter key press in input
            document.getElementById('cityInput').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    document.getElementById('searchBtn').click();
                }
            });

            // Popular cities click handler
            document.querySelectorAll('#popularCities li').forEach(item => {
                item.addEventListener('click', function() {
                    const city = this.getAttribute('data-city');
                    updateWeather(city);
                });
            });
        });
    </script>
</body>
</html>