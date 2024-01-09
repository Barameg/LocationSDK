# LocationSDK For iOS
A framework library that provides iOS with location services such as Search, Geocoding, Routes and ETA

## Credentials
In order to be able to use the framework you must [create account](https://locationservices.barameg.co/signup), once you log in you will have access to your credentials and usage statistics and you will get 200 USD free credit.

You can also check pricing using [our calculator](https://locationservices.barameg.co).

# Services.initSession Method  
## Overview The 
`Services.initSession` method is a part of the Services module and is used to initialize a session with a remote service. This method sends a request to the service, typically an API, using provided credentials (client ID and client key), and it returns session-related data in a JSON string format. 
## Method Signature  
```swift
func initSession( client_id: String, client_key: String ) throws -> String
```
## Parameters

-   `client_id` (String): A unique identifier representing the client or application.
-   `client_key` (String): A security key or token associated with the client.

## Return Value

-   (String): A JSON string containing session-related data.
### Success example
```json
{
	"error": false,
	"message": "Session initiated successfully",
	"data": true
}
```
### Failure example
```json
{
	"error": true,
	"message": "Error_Message",
	"data": false
}
```

## Usage

```swift
do {
    let responseData = try await Services.initSession(
        client_id: "your_client_id",
        client_key: "your_client_key"
    )
    // Process the session-related data in JSON format.
} catch {
    // Handle any errors that may occur during the request.
}
```
## Error Handling
This method can throw errors, so it's essential to implement error handling to manage exceptions that might occur during the request. Ensure that your application gracefully handles potential issues like network errors or invalid input parameters.
## Example
Here's an example of how you can use the `Services.initSession` method to initialize a session with the remote service. The returned JSON data can be parsed and used to establish and maintain a session for subsequent interactions with the service.
```swift
do {
    let responseData = try await Services.initSession(
        client_id: "your_client_id",
        client_key: "your_client_key"
    )
    
    // Parse the JSON data and establish a session for further interactions.
    
} catch {
    // Handle errors, e.g., display an error message to the user.
}
```

# Services.reverseGeocoding Method  
## Overview The 
The `Services.reverseGeocoding` method is a part of the Services module and is used to perform reverse geocoding. It sends a request to a remote service, typically an API, using provided credentials (client ID and client key), latitude, and longitude coordinates. This method retrieves location information based on the provided geographic coordinates and returns the data in a JSON string format.
## Method Signature  
```swift
func reverseGeocoding( 
	client_id: String, 
	client_key: String, 
	language: String, 
	country: String, 
	latitude: String, 
	longitude: String 
) throws -> String
```
## Parameters

-   `client_id` (String): A unique identifier representing the client or application.
-   `client_key` (String): A security key or token associated with the client.
-   `language` (String): The desired language for location information. Typically a two-letter language code (e.g., "en" for English).
-   `country` (String): The target country for location information. Typically a two-letter country code (e.g., "us" for the United States).
-   `latitude` (String): The latitude coordinate of the location to be reverse geocoded.
-   `longitude` (String): The longitude coordinate of the location to be reverse geocoded.
## Return Value

-   (String): A JSON string containing session-related data.
### Success example
```json
{
	"error": false,
	"message": "Request processed successfully",
	"data":{
		"address":"Al Kasr Al Aini, El Sayeda Zeinab, Cairo Governorate, Egypt",
		"latitude":30.033308337581023,
		"longitude":31.150625010171915
	}
}
```
### Failure example
```json
{
	"error": true,
	"message": "Error_Message",
	"data": false
}
```

## Usage

```swift
do {
    let responseData = try await Services.initSession(
        client_id: "your_client_id",
        client_key: "your_client_key",
        language: "en",
        country: "us",
        latitude: "31.150625010171915",
        longitude: "30.033308337581023"
    )
	// Parse the JSON data and display location details to the user.
} catch {
    // Handle any errors that may occur during the request.
}
```
## Error Handling
This method can throw errors, so it's essential to implement error handling to manage exceptions that might occur during the request. Ensure that your application gracefully handles potential issues like network errors or invalid input parameters.
## Example
Here's an example of how you can use the `Services.reverseGeocoding` method to retrieve location information based on provided latitude and longitude coordinates. The returned JSON data can be parsed and used to display location details to the user.
```swift
do {
    let responseData = try await Services.reverseGeocoding(
        client_id: "your_client_id",
        client_key: "your_client_key",
        language: "en",
        country: "us",
        latitude: "31.150625010171915",
        longitude: "30.033308337581023"    
    )
	// Parse the JSON data and display location details to the user.
} catch {
    // Handle errors, e.g., display an error message to the user.
}
```

# Services.searchAutocomplete Method  
## Overview The 
The `Services.searchAutocomplete` method is a part of the Services module and is used to perform location-based autocomplete searches. It sends a request to a remote service, typically an API, using provided credentials (client ID and client key), geographic coordinates, and a search query. This method retrieves autocomplete suggestions based on the provided location and query and returns the data in a JSON string format.
## Method Signature  
```swift
func searchAutocomplete( 
	client_id: String, 
	client_key: String, 
	language: String, 
	country: String, 
	latitude: String, 
	longitude: String,
	query: String
) throws -> String
```
## Parameters

-   `client_id` (String): A unique identifier representing the client or application.
-   `client_key` (String): A security key or token associated with the client.
-   `language` (String): The desired language for autocomplete suggestions. Typically a two-letter language code (e.g., "en" for English).
-   `country` (String): The target country for autocomplete suggestions. Typically a two-letter country code (e.g., "us" for the United States).
-   `latitude` (Double): The latitude coordinate of the location for the autocomplete search.
-   `longitude` (Double): The longitude coordinate of the location for the autocomplete search.
-   `query` (String): The search query for which autocomplete suggestions are requested.
## Return Value

-   (String): A JSON string containing session-related data.
### Success example
```json
{
	"error": false,
	"message": "Request processed successfully",
	"data":[
		{"address":"Damanhour, Naqraha, Damanhour, Egypt"},
		{"address":"Dubai - United Arab Emirates"},
		{"address":"Délices Patisserie Alexandria, Saad Zaghloul, Al Mesallah Sharq, Al Attarin, Egypt"},
		{"address":"Delhi, India"},
		{"address":"Designia Mall, Qetaa at Tarik as Sahrawi, Amreya 1, Egypt"}
	]
}
```
### Failure example
```json
{
	"error": true,
	"message": "Error_Message",
	"data": false
}
```

## Usage

```swift
do {
    let responseData = try await Services.searchAutocomplete(
        client_id: "your_client_id",
        client_key: "your_client_key",
        language: "language_iso_code",
        country: "country_iso_code",
        latitude: "nearby_latitude",
        longitude: "nearby_longitude",
        query: "your_query"
    )
	// Parse the JSON data and display autocomplete suggestions to the user.
} catch {
    // Handle any errors that may occur during the request.
}
```
## Error Handling
This method can throw errors, so it's essential to implement error handling to manage exceptions that might occur during the request. Ensure that your application gracefully handles potential issues like network errors or invalid input parameters.
## Example
Here's an example of how you can use the `Services.searchAutocomplete` method to retrieve autocomplete suggestions based on a specific location and search query. The returned JSON data can be parsed and used to display autocomplete suggestions to the user.
```swift
do {
    let responseData = try await Services.searchAutocomplete(
        client_id: "your_client_id",
        client_key: "your_client_key",
        language: "en",
        country: "us",
        latitude: "31.150625010171915",
        longitude: "30.033308337581023",
        query: "your_query" 
    )
	// Parse the JSON data and display autocomplete suggestions to the user.
} catch {
    // Handle errors, e.g., display an error message to the user.
}
```

# Services.enhancedSearchAutocomplete Method  
## Overview The 
The `Services.enhancedSearchAutocomplete` method is a part of the Services module and is used to perform enhanced, location-based autocomplete searches. It sends a request to a remote service, typically an API, using provided credentials (client ID and client key), geographic coordinates, and a search query in a specified language and country. This method retrieves enhanced autocomplete suggestions based on the provided location and query and returns the data in a JSON string format.
## Method Signature  
```swift
func enhancedSearchAutocomplete( 
	client_id: String, 
	client_key: String, 
	language: String, 
	country: String, 
	latitude: String, 
	longitude: String,
	query: String
) throws -> String
```
## Parameters

-   `client_id` (String): A unique identifier representing the client or application.
-   `client_key` (String): A security key or token associated with the client.
-   `language` (String): The desired language for autocomplete suggestions. Typically a two-letter language code (e.g., "en" for English).
-   `country` (String): The target country for autocomplete suggestions. Typically a two-letter country code (e.g., "us" for the United States).
-   `latitude` (Double): The latitude coordinate of the location for the autocomplete search.
-   `longitude` (Double): The longitude coordinate of the location for the autocomplete search.
-   `query` (String): The search query for which autocomplete suggestions are requested.
## Return Value

-   (String): A JSON string containing session-related data.
### Success example
```json
{
	"error": false,
	"message": "Request processed successfully",
	"data":[
		{
			"address":"مطار برج العرب بالإسكندرية (HBE)، Borg El Arab Airport Rd, Egypt",
			"latitude":30.932410099999998,
			"longitude":29.696463699999999
		},
		{
			"address":"محرم بك، Egypt",
			"latitude":31.183988099999997
			"longitude":29.9364694
		},
		{
			"address":"محطة مصر اسكندرية، Kom Ad Dakah Gharb, Moharam Bek, Egypt",
			"latitude":31.1929786,
			"longitude":29.905251399999997,
		},
		{
			"address":"محطة الرمل، Mahmoud Al Falaki, Al Mesallah Gharb WA Sharif Basha, Al Attarin, Egypt",
			"latitude":31.1972162,
			"longitude":29.8973917
		},
		{
			"address":"موقف محرم بك الجديد, داخل موقف محرم بك الجديد، Ghait Al Enab Sharq, Moharam Bek, Egypt",
			"latitude":31.1776862,
			"longitude":29.914168199999999
		}
	]
}
```
### Failure example
```json
{
	"error": true,
	"message": "Error_Message",
	"data": false
}
```

## Usage

```swift
do {
    let responseData = try await Services.enhancedSearchAutocomplete(
        client_id: "your_client_id",
        client_key: "your_client_key",
        language: "language_iso_code",
        country: "country_iso_code",
        latitude: "nearby_latitude",
        longitude: "nearby_longitude",
        query: "your_query"
    )
	// Parse the JSON data and display enhanced autocomplete suggestions to the user.
} catch {
    // Handle any errors that may occur during the request.
}
```
## Error Handling
This method can throw errors, so it's essential to implement error handling to manage exceptions that might occur during the request. Ensure that your application gracefully handles potential issues like network errors or invalid input parameters.
## Example
Here's an example of how you can use the `Services.enhancedSearchAutocomplete` method to retrieve enhanced autocomplete suggestions based on a specific location, search query, language, and country. The returned JSON data can be parsed and used to display enhanced autocomplete suggestions to the user.
```swift
do {
    let responseData = try await Services.enhancedSearchAutocomplete(
        client_id: "your_client_id",
        client_key: "your_client_key",
        language: "en",
        country: "us",
        latitude: "31.150625010171915",
        longitude: "30.033308337581023",
        query: "your_query"   
    )
	// Parse the JSON data and display enhanced autocomplete suggestions to the user.
} catch {
    // Handle errors, e.g., display an error message to the user.
}
```

# Services.forwardGeocoding Method  
## Overview The 
The `Services.forwardGeocoding` method is a part of the Services module and is used to perform forward geocoding. It sends a request to a remote service, typically an API, using provided credentials (client ID and client key), an address, language, and country. This method retrieves geographic coordinates (latitude and longitude) based on the provided address and returns the data in a JSON string format.
## Method Signature  
```swift
func forwardGeocoding( 
	client_id: String, 
	client_key: String, 
	language: String, 
	country: String, 
	address: String 
) throws -> String
```
## Parameters

-   `client_id` (String): A unique identifier representing the client or application.
-   `client_key` (String): A security key or token associated with the client.
-   `language` (String): The desired language for geocoding results. Typically a two-letter language code (e.g., "en" for English).
-   `country` (String): The target country for geocoding results. Typically a two-letter country code (e.g., "us" for the United States).
-   `address` (String): The address for which geographic coordinates are requested.
## Return Value

- (String): A JSON string containing geographic coordinates (latitude and longitude) based on the provided address.
### Success example
```json
{
	"error": false,
	"message": "Request processed successfully",
	"data":{
		"latitude":31.200106999999999,
		"longitude":29.8995529
	}
}
```
### Failure example
```json
{
	"error": true,
	"message": "Error_Message",
	"data": false
}
```

## Usage

```swift
do {
    let responseData = try await Services.forwardGeocoding(
		client_id: "your_client_id", 
		client_key: "your_client_key", 
		language: "en", 
		country: "us", 
		address: "your_address"
    )
    // Process the session-related data in JSON format.
} catch {
    // Handle any errors that may occur during the request.
}
```
## Error Handling
This method can throw errors, so it's essential to implement error handling to manage exceptions that might occur during the request. Ensure that your application gracefully handles potential issues like network errors or invalid input parameters.
## Example
Here's an example of how you can use the `Services.forwardGeocoding` method to retrieve geographic coordinates (latitude and longitude) based on a specific address. The returned JSON data can be parsed and used to display geocoding results to the user.
```swift
do {
    let responseData = try await Services.forwardGeocoding(
		client_id: "your_client_id", 
		client_key: "your_client_key", 
		language: "en", 
		country: "us", 
		address: "your_address" 
    )
	// Process the geocoding data in JSON format.
} catch {
    // Handle errors, e.g., display an error message to the user.
}
```

# Services.routes Method  
## Overview The 
The `Services.routes` method is a part of the Services module and is used to fetch route data, typically related to geographical locations. This method sends a request to a remote service (presumably an API) to obtain route information and returns the data in a JSON string format.
## Method Signature  
```swift
func routes( 
	client_id: String, 
	client_key: String, 
	language: String, 
	country: String, 
	origin_latitude: String, 
	origin_longitude: String, 
	destination_latitude: String, 
	destination_longitude: String
) throws -> String
```
## Parameters

-   `client_id` (String): A unique identifier representing the client or application.
-   `client_key` (String): A security key or token associated with the client.
-   `language` (String): The desired language for route information. Typically a two-letter language code (e.g., "en" for English).
-   `country` (String): The target country for route information. Typically a two-letter country code (e.g., "us" for the United States).
-   `origin_latitude` (String): The latitude of the starting location.
-   `origin_longitude` (String): The longitude of the starting location.
-   `destination_latitude` (String): The latitude of the destination location.
-   `destination_longitude` (String): The longitude of the destination location.
## Return Value

- (String): A JSON string containing geographic coordinates (latitude and longitude) based on the provided address.
### Success example
```json
{
	"error": false,
	"message": "Request processed successfully",
	"data": [
		{
			"via": "Cairo - Alexandria Desert Rd\/Route 75M",
			"distance":138021,
			"distanceText":"138 km",
			"duration":5948,
			"durationText":"1 hr 39 min",
			"waypoints": [
				[30.359296000000001,30.532789600000001],
				[30.357416300000001,30.531075000000001],
				...
			]
		}, 
		...
	]
}
```
### Failure example
```json
{
	"error": true,
	"message": "Error_Message",
	"data": false
}
```

## Usage

```swift
do {
    let responseData = try await Services.forwardGeocoding(
		client_id: "your_client_id", 
		client_key: "your_client_key", 
		language: "en", 
		country: "us", 
		origin_latitude: "30.932410099999998", 
		origin_longitude: "29.696463699999999", 
		destination_latitude: "30.3593519", 
		destination_longitude: "30.5327214"
    )
	// Process the route data in JSON format.
} catch {
    // Handle any errors that may occur during the request.
}
```
## Error Handling
This method can throw errors, so it's essential to implement error handling to manage exceptions that might occur during the request. Ensure that your application gracefully handles potential issues like network errors or invalid input parameters.
## Example
Here's an example of how you can use the `Services.routes` method to fetch route information for a specific journey. The returned JSON data can be parsed and used to display route details to the user.
```swift
do {
    let responseData = try await Services.forwardGeocoding(
		client_id: "your_client_id", 
		client_key: "your_client_key", 
		language: "en", 
		country: "us", 
		origin_latitude: "30.932410099999998", 
		origin_longitude: "29.696463699999999", 
		destination_latitude: "30.3593519", 
		destination_longitude: "30.5327214"
    )
	// Process the route data in JSON format.
} catch {
    // Handle errors, e.g., display an error message to the user.
}
```
