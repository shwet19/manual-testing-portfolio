# Test Cases: E-Commerce Application (SauceDemo / Dummy Store)

This document contains professional manual test cases designed to validate functional requirements, user authentication boundaries, and edge-case behaviors across core platform modules.

## 1. Authentication Module (Login)

| Test Case ID | Scenario / Objective | Pre-conditions | Test Steps | Input Data | Expected Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_LGN_001** | Verify login with valid credentials (Positive) | User is on the login landing page. | 1. Enter valid username.<br>2. Enter valid password.<br>3. Click 'Login' button. | User: `standard_user`<br>Pass: `secret_sauce` | User is redirected to product dashboard page successfully. | Pass |
| **TC_LGN_002** | Verify login failure with invalid password | User is on the login landing page. | 1. Enter valid username.<br>2. Enter incorrect password.<br>3. Click 'Login' button. | User: `standard_user`<br>Pass: `wrong_pass` | Error message displayed: *"Username and password do not match any user in this service."* | Pass |
| **TC_LGN_003** | Validate empty field handling (Boundary) | User is on the login landing page. | 1. Leave fields entirely blank.<br>2. Click 'Login' button. | User: `[Blank]`<br>Pass: `[Blank]` | Inline validation triggered stating: *"Epic sadface: Username is required."* | Pass |

## 2. Cart & Inventory Module

| Test Case ID | Scenario / Objective | Pre-conditions | Test Steps | Input Data | Expected Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_CRT_001** | Verify item count increments on adding product | User is authenticated on the inventory screen. | 1. Click 'Add to Cart' on first item.<br>2. Observe top header cart badge count. | Product: *Sauce Labs Backpack* | Cart badge count dynamically changes from empty to `1`. | Pass |
| **TC_CRT_002** | Verify persistence of cart items on page refresh | Product is added to the cart badge list. | 1. Add item to cart.<br>2. Trigger manual browser refresh (F5).<br>3. Check cart item total. | N/A | Cart item persistence maintained; count remains `1` after UI reload. | Pass |
| **TC_CRT_003** | Verify structural removal of cart products | User is inside the 'Your Cart' overlay view. | 1. Click the 'Remove' button next to item.<br>2. Verify cart item layout list. | Product: *Sauce Labs Backpack* | Item disappears from the summary screen; badge count decreases to `0`. | Pass |

## 3. End-to-End Checkout Module

| Test Case ID | Scenario / Objective | Pre-conditions | Test Steps | Input Data | Expected Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC_CHK_001** | Validate mandatory field parsing during checkout | Items are added; User is on 'Checkout: Your Info' step. | 1. Fill First/Last Name.<br>2. Leave Postal Code field blank.<br>3. Click 'Continue'. | Name: *Shweta P.*<br>Postal: `[Blank]` | Blocking validation triggered: *"Epic sadface: Postal Code is required."* | Pass |
| **TC_CHK_002** | Verify successful end-to-end checkout completion | User fills all valid shipping details. | 1. Fill all input details.<br>2. Click 'Continue'.<br>3. Verify total price.<br>4. Click 'Finish'. | Postal Code: `411028` | Order summary matches; screen displays: *"Thank you for your order!"* | Pass |
