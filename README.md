# Workshop - React Native Part 1

- [Introduction](#introduction)
  - [Workshop content](#workshop-content)
  - [Documentation](#documentation)
- [Setup](#setup)
- [Step 1 - Fetch the user's coordinates](#step-1---fetch-the-users-coordinates)
  - [Step 1.1 - Use of expo-location with the hook useEffect](#step-11---use-of-expo-location-with-the-hook-useeffect)
  - [Step 1.2 - The useState hook](#step-12---the-usestate-hook)
  - [Step 1.3 - Display of the coordinates](#step-13---display-of-the-coordinates)
- [Step 2 - Current location's weather](#step-2---current-locations-weather)
  - [Step 2.1 - API usage](#step-21---api-usage)
  - [Step 2.2 - Set up the request](#step-22---set-up-the-request)
  - [Step 2.3 - Improve the App component](#step-23---improve-the-app-component)
  - [Step 2.4 - Recap and what we will be doing in the next steps](#step-24---recap-and-what-we-will-be-doing-in-the-next-steps)
  - [Step 2.5 - Create the CurrentWeather component](#step-25---create-the-currentweather-component)
  - [Step 2.6 - Display the image representing the current weather](#step-26---display-the-image-representing-the-current-weather)
- [Bonus - Style](#bonus---style)

## Introduction

### Workshop content

During this workshop, you will learn :

- How to build a weather application in React Native that displays the current weather based on the current location
- How to use Expo to accelerate the development process
- How to interact with an API, here, OpenWeather's one

### Documentation

- [React Native](https://reactnative.dev/docs/getting-started)
- [Expo](https://docs.expo.dev/)
- [Open Weather API](https://openweathermap.org/api)

> Do not hesitate to explore the docs, it could be useful for this workshop

## Setup

Set up you project [here](SETUP.md)

## Step 1 - Fetch the user's coordinates

### Step 1.1 - Use of expo-location with the hook useEffect

In App.js, import everything from expo-location with the following line:

    import * as Location from "expo-location"

You want to fetch the coordinates when the App [component](https://reactnative.dev/docs/intro-react) is mounted, so that's where the [useEffect](https://reactjs.org/docs/hooks-effect.html) hook comes in handy.

Find out how to ask the user to grant you the access to their location.

> *Tip*:
> Even if the user has given his permission, you have to know it by getting their response.
> Your effect should'nt be executed entirely as you want to **wait** for their response
>
> *N.B*: In case of the user denies, just stop the execution of the effect by returning.

### Step 1.2 - The useState hook

Now that you have the permission to access the user's location, find out how to get it and store it **persistently** in your component with the useState hook.

### Step 1.3 - Display of the coordinates

Display the location only if you have access to it, otherwise display an error message.

## Step 2 - Current location's weather

### Step 2.1 - API usage

You will be using the [5 day / 3 hour weather forecast](https://openweathermap.org/forecast5).

- Copy the API call url from the documentation and into a constant variable named API_URL.
- Grab the API key that you have generated previously during the setup and place it in API_URL.

In general, you should'nt directly put your API key in source files since it is private. Instead, you should put it in a .env file. For the sake of this workshop, we will stick to the former, unsafe method.

Currently, the API url is constant, which means that you can't put the latitude and longitude that you want in the URL.

Find out how to modify API_URL to solve this problem.

### Step 2.2 - Set up the request

- Add "https://" at the beginning of the API url
- Update API_URL to get the temperature in Celsius and the language in French

Now that API_URL is set up, create a getWeather that takes the coordinates as a parameter and gets a response from the API.

> *N.B*: In case of error, log it into the console.

### Step 2.3 - Improve the App component

At this point, your App component is only interacting with coordinates if you look at your useEffect hook.

Since you don't need to store the coordinates anymore:

- Update the location state into a boolean named "loading"
- Modify the useEffect hook so that it uses the getWeather function

Based on the name of the new loading state, find a React Native component to replace the error message display

Since you are using the response from the API, store the response's data in a state.

Test if the data is correctly stored by displaying the city's name.

### Step 2.4 - Recap and what we will be doing in the next steps

Great ! You have managed to use the data from the API.

Now you have to create the interface to present all of the information in an appealing manner.

You will create a classic layout with the current weather of the user's location on the top.

### Step 2.5 - Create the CurrentWeather component

Copy the following code into a new file named "CurrentWeather.js" in the components folder.

    import React from 'react'
    import { Text, StyleSheet } from 'react-native'

    export default function CurrentWeather({ data }) {
        return ()
            <>
                <Text>{data?.city?.name}</Text>
            </>
        )
    }

    const styles = StyleSheet.create({
        city: {}
    })

Import that CurrentWeather in App.js and use it in the App component's return.

Now you can display the current temperature thanks to data. However, you need to find the correct object from the list in data. You will need to filter the list and use "dt" (stands for date time).

In a useEffect hook depending on data, store the result of a filter on data.list, in a "currentWeather" state. The filter compares 2 Date objects using the date-fns package:

- the current date time that you construct
- a date time constructed from a dt from the list

> *N.B*: Beware of the timezone and the units

Below the city's name, add:

- The text "Aujourd'hui"
- The rounded temperature in Celsius
- The current weather's description

### Step 2.6 - Display the image representing the current weather

Add an image of representing the current weather above the temperature.

> *N.B*: For the image, use this function
>
>       const getIcons = (icon) => `http://openweathermap.org/img/wn/${icon}@4x.png`

### Bonus - Style

Personalize your weather app by adding style to your components ! (font, size, color, etc)
