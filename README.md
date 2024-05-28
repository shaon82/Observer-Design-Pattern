Introduction
This document provides a comprehensive overview of the weather monitoring system implemented using the Observer design pattern. The system allows multiple display elements to observe weather data changes and update their displays accordingly, ensuring a modular and extensible design.


Class Descriptions
Subject Interface
The Subject interface manages the registration, removal, and notification of observers. It provides the necessary methods to allow observers to subscribe and unsubscribe from updates.

registerObserver(Observer o): Adds an observer to the list.
removeObserver(Observer o): Removes an observer from the list.
notifyObservers(): Notifies all registered observers of state changes.
Observer Interface
The Observer interface defines the method that observers must implement to receive updates from the subject.

update(float temp, float humidity, float pressure): Called when the Subject's state changes, providing the new temperature, humidity, and pressure values.
DisplayElement Interface
The DisplayElement interface defines a method for displaying information. Any class that implements this interface should provide a concrete implementation of the display method.

display(): Outputs the current state of the display.
WeatherData Class
The WeatherData class implements the Subject interface and manages the weather data. It keeps track of a list of observers and notifies them when the weather measurements change.

ArrayList<Observer> observers: Stores registered observers.
registerObserver(Observer o): Adds an observer to the list.
removeObserver(Observer o): Removes an observer from the list.
notifyObservers(): Notifies all registered observers of state changes.
measurementsChanged(): Called when measurements are updated, triggering notifyObservers().
setMeasurements(float temperature, float humidity, float pressure): Sets new measurement values and calls measurementsChanged().
getTemperature(), getHumidity(), getPressure(): Getters for the temperature, humidity, and pressure.
Display Classes
Each display class implements both the Observer and DisplayElement interfaces. They update their state when notified by the WeatherData object and display the updated information.

CurrentConditionsDisplay Class
Displays the current weather conditions.

update(float temperature, float humidity, float pressure): Updates the temperature and humidity, then calls display().
display(): Prints the current temperature and humidity.
StatisticsDisplay Class
Displays average, minimum, and maximum temperatures.

update(float temp, float humidity, float pressure): Updates temperature statistics and calls display().
display(): Prints the average, maximum, and minimum temperatures.
ForecastDisplay Class
Displays a weather forecast based on pressure changes.

update(float temp, float humidity, float pressure): Updates the current and last pressures, then calls display().
display(): Prints a weather forecast based on the pressure trend.
ThirdPartyDisplay Class
Displays custom third-party information based on the weather data.

update(float temperature, float humidity, float pressure): Updates the temperature, humidity, and pressure, then calls display().
display(): Prints the custom third-party information.
