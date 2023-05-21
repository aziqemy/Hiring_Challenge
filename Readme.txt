This document provides an overview of the implementation of a REST API for banking. It outlines the organization of the code, explains how the requirements were implemented, and highlights any relevant decisions made during the development process. Additionally, it includes relevant
diagrams to describe the architecture, data modeling. I'm sorry i dont have knowledge for spring libaries,kafka. I have knowledge for .net core. 
I'm creating this test using .net core rest api with MySQL to store the data. If I got hire to work in synpulse8, i will study and learn whatever tools
or frameworks used by the company before my first day. 


1. Code Organization:

    The code for the REST API is organized using a layered architecture pattern, separating concerns and 
	promoting modularity and maintainability. The following layers are implemented :
	
	a) Presentation Layer: Contains the API controllers responsible for handling incoming HTTP requests and returning 
						appropriate responses.
    b) Business Layer: Implements the business logic and handles the processing of requests from the presentation layer.
	c) Data Access Layer: Provides access to the underlying data source (MySQL database).
	d) Caching Layer: Implements caching mechanisms, such as MemoryCache or Redis, to store frequently accessed data and 
						improve performance.
	e) External Services Layer: Integrates with external services, such as the third-party API for exchange rates.
	
2. Data Modeling:

	The data model for the banking API includes the following entities:

	a)UserLogin: Represents a banking customer with attributes like username/password.
	c)Transaction: Represents a money account transaction with attributes like unique identifier, amount with currency, account IBAN, value date, and description.
					[Insert a data model diagram illustrating the entities and their relationships]

3. Security (Authentication and Authorization):

	a) 	The API implements authentication using JWT (JSON Web Tokens). The client is responsible for obtaining a JWT token by 
		authenticating with the system through a separate authentication mechanism (e.g., username/password).
	b	Upon receiving a request, the API validates the JWT token's signature to ensure its authenticity and integrity. 
		The user's unique identity key is extracted from the token and used for further authorization and processing.
		
4. Caching:

	a) Caching is implemented to improve performance by storing frequently accessed data in memory or a distributed cache.
	b) The API uses caching mechanisms like MemoryCache to store and retrieve data.
	c) The cache is configured to have an appropriate expiration time based on data usage patterns. 
		Cache keys are generated using relevant information, such as customer ID and month, to ensure unique caching for different data sets.
	d) Before accessing the underlying data source (MySQL), the API checks if the requested data is available in the cache. 
		If found, the cached data is returned directly, reducing the need for database queries.
	
5. Logging and Monitoring:

	a) The API incorporates logging and monitoring to track system behavior and detect any anomalies or errors.
	b) Logging frameworks log4net are used to capture important events, exceptions, and diagnostic information.
	
6.Documentation:

	a) The API is documented using Swagger to provide a clear understanding of the available endpoints, their parameters, and expected responses.