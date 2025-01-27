# WordFinderAPI

## Description 

WordFinderAPI is a Dockerized .NET  API crafted to tackle 2D string searches, as part of the QU Beyond developer challenge. I've containerized everything to make it easy for the engineers reviewing the solution.

### System Overview:

Here's a quick look at what's inside:

1. WordFinderAPI: Handles the WordFinder logic for QU Beyond Challenge. I implemented one Thread to find words Vertically and other Thread to find words horizontally.
2. Redis: Boosts WordFinderAPI's performance. I check if Matrix word stream exists on Redis
3. Keycloak: Keeps WordFinderAPI secure with custom policies. 
I validate Request authentication and also validates request Model(FluentValidator).
4. Unit Tests

### Development Environment Setup 

To get things rolling, make sure you've got these tools in your toolkit:

1. Docker - You can download and install Docker from [docker.com](https://www.docker.com/products/docker-desktop).

### Running the Local Environment 

Ready to fire things up locally? Just follow these simple steps:

1. Open a terminal and navigate to the root folder of the project.

2. Now, let's kickstart the local development environment with this command:

   ```bash
   docker-compose -f run-development.yml up -d

### Generating Auth Tokens 

To interact with the WordFinderAPI, you'll need an authorization token from our Keycloak service. It's easy, just follow these steps:

1. Replace the placeholders {USERNAME} and {PASSWORD} with your Keycloak username and password in the following curl command:

   ```bash
   curl --location --request POST 'http://localhost:8080/realms/wordfinder/protocol/openid-connect/token' \
    --header 'Content-Type: application/x-www-form-urlencoded' \
    --data-urlencode 'grant_type=password' \
    --data-urlencode 'client_id=word-finder-client' \
    --data-urlencode 'username={USERNAME}' \
    --data-urlencode 'password={PASSWORD}' \
    --data-urlencode 'scope=openid'

When making requests to the WordFinderAPI, include the "Authorization" header with the prefix "Bearer " followed by your generated token

### Documentation 

For a comprehensive list of available endpoints, along with their request bodies and parameters, head over to:
http://localhost:3000/swagger/index.html (Remember to have your local environment runnning)

### Running Tests 

I made some unit ests to verify it. To run these tests and ensure everything's smooth, follow these simple steps:

1. Navigate to the project's root folder.
2. Jump into the WordFinderAPI.UnitTest folder:
   ```bash
   cd WordFinderAPI.UnitTest
3. Execute the tests using this command:
   ```bash
   dotnet run test
