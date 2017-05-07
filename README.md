# Geocoder

[![Build Status](https://travis-ci.org/kelvins/geocoder.svg?branch=master)](https://travis-ci.org/kelvins/geocoder)
[![Coverage Status](https://coveralls.io/repos/github/kelvins/geocoder/badge.svg?branch=master)](https://coveralls.io/github/kelvins/geocoder?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/kelvins/geocoder)](https://goreportcard.com/report/github.com/kelvins/geocoder)

GoLang package that provides an easy way to use the Google Geocoding API.

See more information about the **Google Geocoding API** at the following link: https://developers.google.com/maps/documentation/geocoding/start

You can use go get:

```
go get github.com/kelvins/geocoder
```

## Usage

Example of usage:

``` go
package main

import (
	"fmt"

	"github.com/kelvins/geocoder"
)

func main() {
	// This example should work without need of an API Key,
	// but when you will use the API in your project you need
	// to set your API KEY as explained here:
	// https://developers.google.com/maps/documentation/geocoding/get-api-key
	// geocoder.ApiKey = "YOUR_API_KEY"

	// See all Address fields in the documentation
	address := geocoder.Address{
		Street:  "Central Park West",
		Number:  115,
		City:    "New York",
		State:   "New York",
		Country: "United States",
	}

	// Convert address to location (latitude, longitude)
	location, err := geocoder.Geocoding(address)

	if err != nil {
		fmt.Println("Could not get the location: ", err)
	} else {
		fmt.Println("Latitude: ", location.Latitude)
		fmt.Println("Longitude: ", location.Longitude)
	}

	// Set the latitude and longitude
	location = geocoder.Location{40.775807, -73.976320}

	// Convert location (latitude, longitude) to address
	addresses, err := geocoder.GeocodingReverse(location)

	if err != nil {
		fmt.Println("Could not get the addresses: ", err)
	} else {
		// Browse all results
		//for _, address := range addresses {
		//	fmt.Println(geocoder.FormatAddress(address))
		//}
		fmt.Println(geocoder.FormatAddress(addresses[0]))
		fmt.Println(addresses[0].FormattedAddress)
		fmt.Println(addresses[0].Types)
	}
}
```

Results:

```
Latitude:  40.7758882
Longitude:  -73.9764703
115, Central Park West, Manhattan, 10023, New York, New York County, New York, United States
115 Central Park West, New York, NY 10023, USA
street_address
```

## General

#### Geocoder

> [Geocoder (noun): A piece of software or a (web) service that implements a geocoding process i.e. a set of interrelated components in the form of operations, algorithms, and data sources that work together to produce a spatial representation for descriptive locational references.](https://en.wikipedia.org/wiki/Geocoding)

#### Geocoding

> [Geocoding is the process of converting addresses (like a street address) into geographic coordinates (like latitude and longitude), which you can use to place markers on a map, or position the map.](https://developers.google.com/maps/documentation/geocoding/start)

#### Reverse Geocoding

> [Reverse geocoding is the process of converting geographic coordinates into a human-readable address. The Google Maps Geocoding API's reverse geocoding service also lets you find the address for a given place ID.](https://developers.google.com/maps/documentation/geocoding/start)

#### Application Programming Interface (API)

> [Application Programming Interface (API) is a set of subroutine definitions, protocols, and tools for building application software. In general terms, it is a set of clearly defined methods of communication between various software components. A good API makes it easier to develop a computer program by providing all the building blocks, which are then put together by the programmer.](https://en.wikipedia.org/wiki/Application_programming_interface)

## Documentation

You can access the full documentation here: [![GoDoc](https://godoc.org/github.com/kelvins/geocoder?status.svg)](https://godoc.org/github.com/kelvins/geocoder)

## License

This project was created under the **MIT license**. You can read the license here: [![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](LICENSE)

Feel free to contribute by commenting, suggesting, creating issues or sending pull requests. Any help is welcome.

## Contributing

1. Create an issue (optional)
2. Fork the repo
3. Make your changes
4. Commit your changes (`git commit -am 'Some cool feature'`)
5. Push to the branch (`git push origin master`)
6. Create a new Pull Request
