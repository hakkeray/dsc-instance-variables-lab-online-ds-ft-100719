
# Instance Variables - Lab

## Introduction
In this lab, you'll practice using instance variables, which you use to store information about a particular instance object. You will continue to use our `fuber` theme and create some methods that operate on our instance variables to return some valuable information about the passenger and driver instance objects.

## Objectives

You will be able to:

* Define and call an instance method
* Define and access instance attributes

## Instructions

Below, define classes for both a Driver and a Passenger -- for now just define the classes and remember to include the keyword `pass` so that you'll have valid syntax for our classes.


```python
# Driver class
class Driver(object):
    pass
```


```python
# Passenger class
class Passenger(object):
    pass
```

Next, instantiate a new instance of a passenger and a new instance of a driver. Give the passenger a `rating` of `4.9` and give the driver a `miles_driven` attribute of `100,000`.


```python
driver = Driver() # assign a driver instance
# give the driver instance object 'miles_driven' of 100000

driver.miles_driven = 100000

passenger = Passenger() # assign the passenger instance
# give the passenger instance object a 'rating' of 4.9
passenger.rating = 4.9
```

Your next challenge is to build a function to find a driver with a given name. The function should take two inputs: drivers and search_name. Drivers will be a list of driver objects (instances of the class you defined above) and search_name will be a string for the driver name you wish to search from. The function should then return the first driver object from drivers whose name is an exact match to the search name. If there is no driver that matches the name searched for, then the function should return `None` and print a string stating "Sorry we couldn't find a driver with the name, ____! :\(" For example, if there were no results for the search name "Jack" your function should return None and print:

```python
"Sorry we couldn't find a driver with the name, Jack! :("
```


```python
def find_driver_by_name(drivers, name):
    # write your code here
    for driver in drivers:
        if driver.name  == name:
            return driver
    print("Sorry we couldn't find a driver with the name, {}! :(".format(name))
    return None
```


```python
alex_driver = Driver()
alex_driver.name = "alex"
alex_driver.rating = 9.0
michelle_driver = Driver()
michelle_driver.name = "michelle"
michelle_driver.rating = 8.0
jake_driver = Driver()
jake_driver.name = "jake"
jake_driver.rating = 9.7
ashleigh_driver = Driver()
ashleigh_driver.name = "ashleigh"
ashleigh_driver.rating = 8.75
list_of_drivers = [alex_driver, michelle_driver, jake_driver, ashleigh_driver]
```

To test your function, here's some arbitrary definitions to create instances of your Driver class. Run the cells below. 


```python
output = find_driver_by_name(list_of_drivers, "jake")
output
```




    <__main__.Driver at 0x10d451048>




```python
output = find_driver_by_name(list_of_drivers, "michelle")
output
```




    <__main__.Driver at 0x10d451710>




```python
output = find_driver_by_name(list_of_drivers, "allison")
output
```

    Sorry we couldn't find a driver with the name, allison! :(


If you've correctly coded the find driver by name function, then the first two calls should have returned Driver objects, while the third should have printed the apology statement and returned `None`. (You can further inspect the final output to verify this using the type() method which should reveal that the output is indeed a `Nonetype`; a plain call to output as written above returns nothing.


While perhaps moderately useful, the function as written is rather brittle. Misspelling a driver's name will lead to no results. As such, write a more general method called `name_starts_with()` that will return a list of instance objects that start with a given substring. For example, you could pass the function a substring 'a' to return all drivers whose name begins with a.


```python
# write your method here that returns the list of 
# drivers whose name starts which the given substring
def name_starts_with(drivers, substring):
    starts_with_a = []
    for driver in drivers:
        if substring in driver.name:
            starts_with_a.append(driver)
    
    return starts_with_a
```

Finally, define a method that returns the driver with the highest rating.


```python
# write your method here that returns the driver with the highest rating
def highest_rated_driver(drivers):
    highest_rating = drivers[0].rating
    best_driver = drivers[0]
    
    for driver in drivers:
        if driver.rating > highest_rating:
            best_driver = driver
            highest_rating = driver.rating
    
    return best_driver
```

## Bonus

Define a `NewDriver` class with an instance method called, `passenger_names`. Then, instantiate a new instance of the NewDriver class called `best_driver` that has the attributes `name`, `car_make`, `car_model`, `age`, and `passengers`. The `passengers` attribute will point to the list of passenger instances, which is provided below as `list_of_passengers`:


```python
class NewDriver:
    
    def passenger_names(self):
        names = []
        for passenger in self.passengers:
            names.append(passenger.name)
        return names
```


```python
alex_passenger = Passenger()
alex_passenger.name = "alex"
michelle_passenger = Passenger()
michelle_passenger.name = "michelle"
jake_passenger = Passenger()
jake_passenger.name = "jake"
ashleigh_passenger = Passenger()
ashleigh_passenger.name = "ashleigh"
list_of_passengers =  [alex_passenger, michelle_passenger, jake_passenger, ashleigh_passenger]
```


```python
best_driver = NewDriver() # instantiate a NewDriver instance object
# add the name attribute and assign it 'Garol'
best_driver.name = 'Garol'
# add the car_make attribute and assign it 'toyota'
best_driver.car_make = 'toyota'
# add the car_model attribute and assign it 'camry'
best_driver.car_model = 'camry'
# add the age attribute and assign it '30'
best_driver.age = '30'
# add the passengers attribute and assign it to the list_of_passengers
best_driver.passengers = list_of_passengers
```

Alright, great! Now you have some attributes on the driver that you can work with. Create an instance method in the NewDriver class called `passenger_names` which returns a list of all the passengers' names/
Your output should look like `['alex', 'michelle', 'jake', 'ashleigh']`.


```python
names_of_passengers = best_driver.passenger_names() # assign the return of best_driver.passenger_names()
print(names_of_passengers)
```

    ['alex', 'michelle', 'jake', 'ashleigh']


If you would like to see a more formatted list, try calling the method below on the best_driver instance:


```python
def display_names():
    i = 1
    for name in best_driver.passenger_names():
        print("{}. {}".format(i, name))
        i += 1

# call display_names to see a formatted list of names
display_names()
```

    1. alex
    2. michelle
    3. jake
    4. ashleigh


Neat -- great work! 

## Summary

In this lab, you practiced creating instance variables that add information to our instance objects. You then used these instance methods to return information about the instances themselves.
