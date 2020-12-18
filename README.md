# API-Mapty

Link: https://olaknowct.github.io/API-Mapty/

## Description

- API-Mapty Allows you to plot all workouts using Geolocation API and leaflet 3rd party map library

## How it works
1. As the page loads, allow the browser to access your location
2. Click any(desired) point location on Map
3. A form record will be displayed upon clicking anywhere
4. Submit and the app will auto plot the details from the form and geolocation coordinates


## About

- The Project is used for educational purposes only, its part of the lesson i took from Jonas.
- As part of my learnings and would benefit me, I've listed down here **(See features section)** all the PSEUDO Code, SUMMARY and Feautures from this Project
- I've documented as well the events used on this project and API used to bind the coordinates onto map
- The Project uses Object Oriented Programming as its Architecture.   

### Features, PSEUDO, Summary And Learnings

	- Create new instance of App
	- Initialized map by using geolocation map
		○ Render Map
			§ Save objects to map global variable
	- Add click on the map event listener
		○ When map clicked
			§ Show form and focus to distance
			§ Get and save clicked coordinates on mapEvent global variable
	- Add submit event listener from the form
		○ When form submitted
			§ Validate data using helper function (to make it more clean)
				□ Accepts negative/positive elevation if type is cycling 
				□ Accepts positive integer only if type is running
			§ Create new instance object based from the type
				□ Cycling or Running
			§ Add New objects to global workouts array
			§ Render Workout Marker
				□ Render based from the type
				□ Render based from the coordinates
				□ Render it to the map created from the initialization 
			§ Render workout list
				□ Set the common html structure
				□ Add html content based from type
				□ DOM : insert adjacent html on the form
			§ Hide form and Clear form input data
				□ Remove transition by setting style to none and set back to grid after
				□ Add class hidden to form
			§ Set local storage for persisting data
				□ Not advisable for big data
				□ Setting all workouts array into local storage
				□ Use json stringify to convert it into string
	- Add click event listener to unorder link element
		○ When ul element clicked
			§ Find its data-id using event delegation 
				□ Event delegation are useful when the element doesn’t exist
				□ Use closest to parent to determine its dateset id
			§ Find the workout data based from the dataset id of being clicked
			§ Use workout data coordinates to move to pin point
				□ Use Leaflet to move on certain point using setView
	- Get local storage
		○ Parse local storage
			§ If null do nothing
			§ Parsing and stringify let the prototype chain unavailable
				□ All parents methods/properties will not be inherited
		○ Store it to workouts array
		○ Loop thru each array and reuse render workout on list
		○ Asynchronously render workout on map 
			§ This is done only after the maps loaded
	- Resetting of local storage
		○ Remove local storage data using key
    ○ Reload the page 


## API Used
	- https://leafletjs.com/
		○ 3rd Party Library
		○ Mobile-friendly interactive maps
		○ Used a host version
		○ Delegated an event listener to method of MAP called on
    
## Event Listener
	- Load Page
	- Receive Position
		○ Geolocation API
	- Click on Map
		○ Leaflet, a third party library, handles it
	- Change input
		○ 'change' events
		○ For cycling and running
		○ Submit Form
