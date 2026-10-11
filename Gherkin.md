# Gherkin Keywords and Simple Examples

Gherkin is a plain-language way to describe application behavior. It uses keywords such as Feature, Scenario, Background, Given, When, Then, And, But, Scenario Outline, and Examples.

## Core Keywords

- Feature
- Scenario
- Scenario Outline
- Examples
- Background
- Given
- When
- Then
- And
- But

## Simple Example 1: Basic Scenario

```gherkin
Feature: Login to the application

Background:
  Given the user is on the login page

Scenario: Successful login
  When the user enters a valid username and password
  And clicks the login button
  Then the user should be redirected to the dashboard

Scenario: Invalid login
  When the user enters a wrong password
  And clicks the login button
  Then an error message should be displayed
  And the user should remain on the login page
```

## Example Using And and But

```gherkin
Feature: Shopping cart

Scenario: Add an item to the cart
  Given the user is viewing a product page
  And the product is in stock
  When the user clicks "Add to cart"
  Then the item should appear in the cart
  And the cart count should increase by 1

Scenario: Cannot add an out-of-stock item
  Given the user is viewing a product page
  And the product is out of stock
  When the user clicks "Add to cart"
  Then the item should not be added to the cart
  But a message should say the item is unavailable
```

## Example Using Background

```gherkin
Feature: User profile

Background:
  Given the user is logged in
  And the user is on the profile page

Scenario: View profile details
  Then the user's name should be visible
  And the email address should be visible

Scenario: Edit profile
  When the user changes the display name
  And saves the profile
  Then the updated name should be displayed
```

## Example Using Scenario Outline and Examples

```gherkin
Feature: Calculator

Scenario Outline: Add two numbers
  Given I have entered <first> into the calculator
  And I have entered <second> into the calculator
  When I press add
  Then the result should be <result>

Examples:
  | first | second | result |
  | 2     | 3      | 5      |
  | 5     | 4      | 9      |
  | 10    | 7      | 17     |
```

## Example Showing All Keywords Together

```gherkin
Feature: Pet adoption form

Background:
  Given the user is on the adoption page

Scenario: Adopt a dog
  Given the user selects a dog from the list
  When the user fills in the required details
  And submits the form
  Then the adoption request should be created
  And a confirmation message should be shown
  But the user should not see a validation error

Scenario Outline: Pet adoption validation
  Given the user enters <name> as the pet name
  And the user chooses <petType>
  When the user submits the form
  Then the result should be <status>

Examples:
  | name | petType | status   |
  | Max  | Dog     | success  |
  |      | Cat     | failure  |
  | Luna |         | failure  |
```

## Quick Summary

- Feature describes the overall behavior.
- Scenario describes a specific example.
- Background runs before each scenario.
- Given sets the starting state.
- When describes the action.
- Then describes the expected result.
- And adds more conditions or steps.
- But adds a negative condition or exception.
- Scenario Outline lets you reuse the same test with multiple inputs.
- Examples provide the data values for the outline.

These examples are intentionally simple so they are easy to read and easy to learn.