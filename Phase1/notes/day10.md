BUG-S01: Product images don’t match product names on the inventory page
Field	Details
Environment	Chrome (latest), Windows 11, https://www.saucedemo.com
Severity / Priority	Major / Medium
Steps	1. Open saucedemo.com 2. Log in as problem_user / secret_sauce 3. Look at the product list on the Products page
Expected	Each product shows its own image (e.g., “Sauce Labs Backpack” shows a backpack)
Actual	Products show the wrong image (the same dog photo or an image from a different item). Reproducible every time
Evidence	Screenshot of the product grid; compare with standard_user (images correct)
BUG-S02: “Remove” button does not remove an item from the cart
Field	Details
Environment	Chrome (latest), Windows 11
Severity / Priority	Major / High
Steps	1. Log in as problem_user 2. Click Add to cart on “Sauce Labs Backpack” 3. Click Remove on the same product (on the product list or in the cart)
Expected	Item is removed; the cart badge count decreases; the button returns to “Add to cart”
Actual	The item stays in the cart and the badge count does not drop. Reproducible every time
Evidence	Screen recording of the add and remove clicks; screenshot of the cart page still listing the item
BUG-S03: Last Name field does not accept input on the checkout page
Field	Details
Environment	Chrome (latest), Windows 11
Severity / Priority	Critical / High (blocks purchase)
Steps	1. Log in as problem_user 2. Add any item to the cart 3. Open the cart, click Checkout 4. Type “Kumar” in Last Name 5. Fill First Name and Postal Code, click Continue
Expected	Last Name accepts the text and the user reaches the order overview
Actual	The Last Name field does not take the typed text, so the form fails with “Last Name is required” and the user cannot check out
Evidence	Screen recording showing the typing; screenshot of the error. Note that First Name and Postal Code work, which isolates the problem to one field



BUG-D01: Invalid email shows only a red border, with no error message
Field	Details
Page	https://demoqa.com/text-box
Environment	Chrome (latest), Windows 11
Severity / Priority	Minor / Low
Steps	1. Open the Text Box page 2. Enter Ravi in Full Name 3. Enter ravi@ in Email 4. Click Submit
Expected	An invalid-email message appears, and the invalid data is not displayed in the output
Actual (to verify)	The field is outlined in red but there is no text message. This is an accessibility issue, because a user relying on colour alone gets no explanation
Evidence	Screenshot of the red border; Elements tab showing the field-error class and no message element
BUG-D02: Fixed ad/footer banner covers the Submit button on the Practice Form
Field	Details
Page	https://demoqa.com/automation-practice-form
Environment	Chrome, 1366x768 window
Severity / Priority	Major / Medium
Steps	1. Open the Practice Form 2. Fill the required fields 3. Scroll to the bottom and try to click Submit
Expected	Submit is fully visible and clickable
Actual (to verify)	A fixed banner overlaps the button at some window sizes, so the click lands on the banner instead. Many automation users see this as “element click intercepted”
Evidence	Screenshot showing the overlap; Elements tab showing the banner’s position: fixed style; try at a larger window size to isolate it
BUG-D03: Date of Birth accepts a future date
Field	Details
Page	https://demoqa.com/automation-practice-form
Environment	Chrome (latest), Windows 11
Severity / Priority	Minor / Low
Steps	1. Fill all required fields 2. Click Date of Birth, choose a date in the year 2035 (or type it) 3. Click Submit
Expected	A date of birth in the future is rejected or not selectable
Actual (to verify)	The form is submitted and the confirmation modal shows the future date
Evidence	Screenshot of the modal showing the future date 