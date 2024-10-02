# API Testing - Restful Booker

## Project Overview
This project involves automating API testing for the Restful Booker platform using Postman. The primary goal is to ensure that the API endpoints function correctly by validating requests, responses, and error handling. The testing covers scenarios such as GET, POST, PUT, DELETE requests to various endpoints, handling authentication, and verifying data integrity across the API.

## Test Plan

### 1. Objective
The primary objective of this project is to validate the API endpoints of the Restful Booker platform. This includes:
- Checking API responses
- Ensuring the API meets business requirements
- Identifying and reporting any failures or issues

### 2. Scope
The scope of this testing project includes:
- Functional testing of API endpoints
- Validation of different HTTP methods (GET, POST, PUT, DELETE)
- Response code and data validation
- Error handling and boundary condition testing

### 3. Test Strategy
- **Tools:** Postman is used for API testing, with automated tests written in JavaScript.
- **Test Types:**
  - Functional Testing
  - Boundary Testing
  - Authentication and Authorization Testing
  - Negative Testing for error scenarios

### 4. Test Environment
- **Postman workspace**: Separate collections are created for each API endpoint.
- **API documentation**: Provided by the Restful Booker platform.

### 5. Entry/Exit Criteria
- **Entry Criteria**: APIs must be fully developed, and the API documentation must be available.
- **Exit Criteria**: All test cases must pass, and response validation should meet the expected outcome.

## Test Cases and Results

### Test Case 1: Validate the Booking Object Schema
- **Status**: Pass
- **Description**: Ensure that the booking object conforms to the defined schema.
- **Preconditions**: The booking API endpoint is accessible, and a valid booking object is returned.
- **Steps**:
  1. Send a request to the booking endpoint.
  2. Validate the structure of the booking object against the schema.
- **Expected Result**: The booking object matches the required schema.

```javascript
pm.test("Validate the booking object schema", function () {
    const responseData = pm.response.json();

    pm.expect(responseData).to.be.an('object');
    pm.expect(responseData.booking).to.exist.and.to.be.an('object');
    pm.expect(responseData.booking.firstname).to.exist.and.to.be.a('string');
    pm.expect(responseData.booking.lastname).to.exist.and.to.be.a('string');
    pm.expect(responseData.booking.totalprice).to.exist.and.to.be.a('number');
    pm.expect(responseData.booking.depositpaid).to.exist.and.to.be.a('boolean');
    pm.expect(responseData.booking.bookingdates).to.exist.and.to.be.an('object');
    pm.expect(responseData.booking.bookingdates.checkin).to.exist.and.to.be.a('string');
    pm.expect(responseData.booking.bookingdates.checkout).to.exist.and.to.be.a('string');
});

## Test Cases and Results

### Test Case 2: Response Status Code is 200
- **Status**: Pass
- **Description**: Verify that the API returns a 200 status code for a successful booking retrieval.
- **Preconditions**: The booking API is functioning and the request is valid.
- **Steps**:
  1. Send a request to the booking endpoint.
  2. Check the response status code.
- **Expected Result**: The status code should be 200.

### Test Case 3: Content-Type is `application/json`
- **Status**: Pass
- **Description**: Ensure that the Content-Type of the response is `application/json`.
- **Preconditions**: The API returns a valid response.
- **Steps**:
  1. Send a request to the booking endpoint.
  2. Check the Content-Type header in the response.
- **Expected Result**: The Content-Type should be `application/json`.

### Test Case 4: Booking ID Should be a Number
- **Status**: Pass
- **Description**: Validate that the booking ID returned in the response is a number.
- **Preconditions**: The API returns a valid booking object.
- **Steps**:
  1. Send a request to retrieve a booking.
  2. Validate the type of the `bookingID` field in the response.
- **Expected Result**: The `bookingID` should be a number.

### Test Case 5: First Name is a Non-Empty String
- **Status**: Pass
- **Description**: Verify that the first name in the booking object is a non-empty string.
- **Preconditions**: The booking object contains user details.
- **Steps**:
  1. Send a request to retrieve a booking.
  2. Check the `firstName` field in the response object.
- **Expected Result**: The `firstName` should be a non-empty string.

### Test Case 6: Last Name is a Non-Empty String
- **Status**: Pass
- **Description**: Verify that the last name in the booking object is a non-empty string.
- **Preconditions**: The booking object contains user details.
- **Steps**:
  1. Send a request to retrieve a booking.
  2. Check the `lastName` field in the response object.
- **Expected Result**: The `lastName` should be a non-empty string.

## Documentation

### Create Booking
This endpoint allows you to create a new booking.

- **Request Body**:
```json
{
  "firstname": "string",
  "lastname": "string",
  "totalprice": 100,
  "depositpaid": true,
  "bookingdates": {
    "checkin": "2024-01-01",
    "checkout": "2024-01-05"
  },
  "additionalneeds": "Breakfast"
}
## Response

```json
{
  "bookingid": 1,
  "booking": {
    "firstname": "John",
    "lastname": "Doe",
    "totalprice": 100,
    "depositpaid": true,
    "bookingdates": {
      "checkin": "2024-01-01",
      "checkout": "2024-01-05"
    },
    "additionalneeds": "Breakfast"
  }
}


