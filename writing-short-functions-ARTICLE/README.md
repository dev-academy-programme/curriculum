# Writing short functions

## Example

Here's an example of some old JavaScript that could use refactoring:

```javascript
function checkWeather () {
  console.log('Getting weather report...')
  var apiKey = '12345ABCDE';

  $.get('https://api.openweathermap.org/data/2.5/weather?lat=' + 
    loc.coords.latitude + '&lon=' + loc.coords.longitude + '&units=metric',
    function (response) {
      var weather = response.weather[0];
      var celcius = response.main.temp;
      var fahrenheit = celcius * 9 / 5 + 32;

      $('#weather-icon').attr('src', iconBase + weather.icon + '.png');
      $('#weather-description').html(weather.description);
      $('#temp-c').html(Math.floor(celcius) + ' &deg;C');
      $('#temp-f').html(Math.floor(fahrenheit) + ' &deg;F');

      var background = getBackground(weather.id);
      $('body').css('background', 
                    '#fff url('+background[0]+') no-repeat');
      $('body').css('background-size', 'cover');
      $('#attribution').html('Photo: ' + background[1]);
    }
  );
}
```
There's a lot going on here! It does make use of an external function (`getBackground`) but even so, could be significantly refactored. Its name is quite vague (`checkWeather`), and it actually does quite a bit more than check the weather!


## Use named functions where possible

Inline anonymous functions like this one can be very useful:

```javascript
  var arr = [1, 2, 3]
  var incremented = arr.map(function (n) {
    return n + 1
  })
```

Here we pass an anonymous function to `map`, and although we could in theory give it a name it wouldn't make much difference:

```javascript
  var incremented = arr.map(addOne)

  function addOne (n) {
    return n + 1
  }
```

However, when a function is larger and more complex it can make your code more legible to give it its own name and separate it out:

```javascript
  $.get('https://api.openweathermap.org/data/2.5/weather?lat=' + 
    loc.coords.latitude + '&lon=' + loc.coords.longitude + '&units=metric',
    processWeatherData);
  );

  function processWeatherData (data) {
    var weather = data.weather[0];
    var celcius = data.main.temp;
    var fahrenheit = celcius * 9 / 5 + 32;

    $('#weather-icon').attr('src', iconBase + weather.icon + '.png');
    $('#weather-description').html(weather.description);
    $('#temp-c').html(Math.floor(celcius) + ' &deg;C');
    $('#temp-f').html(Math.floor(fahrenheit) + ' &deg;F');

    var background = getBackground(weather.id);
    $('body').css('background', 
                  '#fff url('+background[0]+') no-repeat');
    $('body').css('background-size', 'cover');
    $('#attribution').html('Photo: ' + background[1]);
  }
```

This accomplishes two goals: we give our code a descriptive name, and we make it possible to _re-use_ the function if another area of our project can make use of it.


## Use short functions

`processWeatherData` still seems long and complex, however. Maybe we can trim it down a bit...

```javascript
  function processWeatherData (data) {
    var weather = data.weather[0];
    displayWeather(weather)
    displayTemperature(data.main.temp)
  }

  function displayWeather (weather) {
    $('#weather-icon').attr('src', iconBase + weather.icon + '.png');
    $('#weather-description').html(weather.description);
    var background = getBackground(weather.id);
    $('body').css('background', 
                  '#fff url('+background[0]+') no-repeat');
    $('body').css('background-size', 'cover');
    $('#attribution').html('Photo: ' + background[1]);
  }

  function displayTemperature (celcius) {
    var fahrenheit = celcius * 9 / 5 + 32;
    $('#temp-c').html(Math.floor(celcius) + ' &deg;C');
    $('#temp-f').html(Math.floor(fahrenheit) + ' &deg;F');
  }

```

It's fair to say that this is roughly the same amount of code, but better organised and easier for others to navigate. There are likely other changes we could make that would improve the situation even further.


## Resources

 * https://silkandspinach.net/2013/01/30/why-shorter-methods-are-better/
 * http://blog.goyello.com/2013/01/21/top-9-principles-clean-code/

