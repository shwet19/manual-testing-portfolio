# Defect Logs & Production Bug Reports (JIRA Simulation Format)

This document displays functional bugs identified during exploratory testing sessions, documented using strict development tracking layouts.

---

### 🐞 BUG-101: Price Total calculation mismatch during multi-item checkouts
* **Project:** Core E-Commerce Platform
* **Issue Type:** Bug / Defect
* **Priority:** High (P2)
* **Severity:** Major (S2)
* **Status:** Open / Unassigned
* **Environment:** Chrome Version 122.0.6261.95 (Official Build), Windows 11 Home

#### 📝 Description:
When a user adds multiple distinct inventory items to their cart, the final "Item total" tax summary listed on the Step Two checkout confirmation layout displays an incorrect mathematical sum (omitting the value of secondary items).

#### 🧪 Steps to Reproduce:
1. Navigate to the base marketplace dashboard screen.
2. Click **"Add to Cart"** on the *Sauce Labs Backpack* (\$29.99).
3. Click **"Add to Cart"** on the *Sauce Labs Bike Light* (\$9.99).
4. Click the cart header container icon to proceed to the review screen.
5. Click **"Checkout"**, input valid customer info strings, and press **"Continue"**.
6. Observe the item value calculations presented directly under the payments segment.

#### 🎯 Actual Result:
The calculation summary displays: `Item total: $29.99`. The cost of the Bike Light (\$9.99) is missing from the checkout math.

#### 🏁 Expected Result:
The text component should read: `Item total: $39.98` (\$29.99 + \$9.99).

---

### 🐞 BUG-102: System crashes on entering highly extended character lengths into checkout forms
* **Project:** Core E-Commerce Platform
* **Issue Type:** Bug / Defect
* **Priority:** Medium (P3)
* **Severity:** Minor (S3)
* **Status:** Open / Unassigned
* **Environment:** Mozilla Firefox v123.0.1, macOS Sonoma

#### 📝 Description:
Input fields on the checkout configuration dashboard do not contain string truncation handling. Pasting more than 500 characters into the First Name field forces a local UI crash block (`HTTP 500 Internals`).

#### 🧪 Steps to Reproduce:
1. Proceed through the core workflows until arriving at checkout forms.
2. In the **"First Name"** component, paste a text string containing exactly 550 characters.
3. Complete remaining parameters with brief placeholder metrics and click **"Continue"**.

#### 🎯 Actual Result:
The interface hangs indefinitely before returning an unhandled server stack dump error page.

#### 🏁 Expected Result:
The UI component should restrict input sizes to a maximum threshold (e.g., 50 characters) or gracefully render a front-end error message stating: *"First name cannot exceed 50 characters."*
