**Errors**

1. Type Mismatch in City Selection (weatherData.country vs weatherData.city)
The Bug: In the cityButton onPress handler and style check, you are comparing and setting selectedCity using weather.country instead of weather.city. Because all three cities are in 'South Africa', selecting one selects all of them or breaks the filtering.
The Fix: Change weather.country to weather.city


2. Missing ImageBackground Import
The Bug: You are using <ImageBackground> in your JSX, but it is never imported from 'react-native'.
The Fix: Add ImageBackground to your React Native imports

3. Duplicate Property Bug in WeatherDetail Component
The Bug: Inside the WeatherDetail component, both text elements display label instead of using value
The Fix: Change the second text tag to output value:


4. Incorrect Key in Sun & Moon Data
The Bug: For the Sunrise detail item, you are passing selectedWeather.sunset
The Fix: Pass selectedWeather.sunrise instead:

TypeScript
<WeatherDetail label="Sunrise" value={selectedWeather.sunrise} />


5. Infinite Scroll / Layout Crash in Hourly Forecast
The Bug: The hourly forecast ScrollView has horizontal={false} (rendering vertically) inside a parent ScrollView that is also vertical. Furthermore, the hourTemperature text displays selectedWeather.temperature (the city's current overall temperature) rather than the individual hour's temperature (hour.temperature).
The Fix: Set horizontal={true} and fix the temperature mapping

6. Missing return Statement in 5-Day Forecast Map
The Bug: Inside the selectedWeather.daily.map(...) callback, you used curly braces {} without an explicit return statement, meaning nothing renders for the 5-day forecast.
The Fix: Add a return keyword or replace the curly braces with parentheses ()

The Bug: In dailyTemperatures, the low temperature is rendered first, and the high temperature second. Also, the dailyCard layout uses flexDirection: 'column', but the child elements use explicit widths (width: 45, width: 90, flex: 1) which overlap or clip text in React Native.
The Fix: Change the row layout to horizontal so elements align nicely side-by-side

**Evidence**

<img width="1080" height="2400" alt="Screenshot_20261010_112259" src="https://github.com/user-attachments/assets/dd9e8ad7-5c75-4ff3-9a25-d1ee0b86bea7" />
