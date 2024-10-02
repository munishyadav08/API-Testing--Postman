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


Make sure to replace `./path_to_your_image/api.png` with the actual path of your image after adding it to the appropriate directory in your project folder.

This README is now updated to include the new schema validation code and the screenshot for clarity.

