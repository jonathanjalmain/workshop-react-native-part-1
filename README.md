# Workshop - React Native Part 1

- [Introduction](#introduction)
  - [Workshop content](#workshop-content)
  - [Documentation](#documentation)
- [Setup](#setup)
- [Presence](#presence)

## Introduction

### Workshop content

During this workshop, you will learn :

- How to build a weather application using React Native that displays the current weather based on the current location
- How to use Expo Snack to accelerate the development process :
- How to interact with an API (OpenWeather)

### Documentation

Read the React Native documentation [here](https://reactnative.dev/docs/getting-startedd)

## Setup

Set up you project [here](SETUP.md)

## Presence

To be marked present, you need to send us a mail with your work, using your Epitech email address.

Please respect the following format :

- **To**: <christian.tran@epitech.eu>
- **Cc**: <hahrin.seo@epitech.eu>
- **Subject:** [First Name] [LAST NAME] Workshop React Native Part 1
- **Body:** [URL of your snack]

## Step 1 - Fetch the user's coordinates

### Step 1.1 - Use of expo-location with the hook useEffect

In App.js, import everything from expo-location with the following line:

    import * as Location from "expo-location"

You want to fetch the coordinates when the App [component](https://reactnative.dev/docs/intro-react) is mounted (created), so that's where [useEffect](https://reactjs.org/docs/hooks-effect.html) come in handy.

You can either use this hook like this:

    React.useEffect(() => {}, [])

or like that by importing useEffect from 'react'

    useEffect(() => {}, [])

Either way is fine but I find the latter cleaner. Thus, the first line would look like this:

    import React, { useEffect } from 'react';

You can see that this hook requires 2 parameters:

- The first one is a side effect (function)
- The second parameter is an array that contains variables. Whenever one of these variables' value changes, the side effect is executed

Since we only need to call the side effect **once** when the component is created, we can just leave an empty array.


#### Exercice

Find the method from expo-location that allows you to get the user's permission to access their location

