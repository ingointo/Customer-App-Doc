### DanatCareUae 

### Bottom Tabs
#### **1. Home Screen**
The Home Screen provides users with an overview of current offers, order tracking, and a chat option. It also includes product categories for easy navigation.

**Components:**
- **TabHeader:** Displays the title "Home" and is persistent across all tab screens.
- **SearchProducts:** Allows users to search for products, with navigation triggered by pressing the search bar.
- **HomeCarouselPagination:** Showcases a carousel of offers or featured products.
- **CustomHomeRow:** A set of clickable options for "Today's Offers," "Track My Order," and "Chat with Us," each with unique colors, icons, and actions.
- **Categories Component:** Displays the product categories using the `Categories` component.
- **ExitAlertModal:** Modal that appears when users attempt to exit the app, confirming their intent to close the application.

**Key Functions:**
- **handleBackPress:** Handles the back button press to trigger the exit alert modal.
- **handleAppStateChange:** Monitors app state to hide the exit alert when the app becomes active again.

#### **2. Categories Screen**
The Categories Screen allows users to browse and search for products based on predefined categories.

**Components:**
- **TabHeader:** Displays the title "Categories."
- **SearchContainer:** Allows users to search for categories.
- **Categorie:** Fetches and lists categories filtered by the search query.

**Key Functions:**
- **setSearchText:** Updates the search text state for filtering categories.

#### **3. My Orders Screen**
The My Orders Screen allows users to view their past and active sales order quotations.

**Components:**
- **TabHeader:** Displays the title "Orders."
- **SearchContainer:** Allows users to search for their orders.
- **FlatList:** Displays a list of orders with pagination for lazy loading.
- **OrdersList:** Renders each order item with relevant details such as order ID, status, and date.

**Key Functions:**
- **fetchData:** Fetches quotation data using an API and updates the order list dynamically.
- **handleEndReached:** Loads additional orders when the user reaches the end of the current list.

#### **4. Cart Screen**

The Cart Screen allows users to review and manage the products added to their cart, update quantities, remove items, and place an order. It also provides an overview of the total price before proceeding to checkout.

**Functions and Key Features:**  
1. **Cart Data Fetching:**  
   - Retrieves cart items from the Redux store (`cartItems`), displaying them with product images, names, prices, and expected prices.

2. **Price Calculation (`useEffect`):**  
   - Automatically calculates and updates the total cart price based on the individual item prices and their quantities.

3. **Warehouse Fetching (`useEffect`):**  
   - Fetches available warehouse data using `fetchWarehouse` API call and updates the `warehouse` state for order placement.

4. **Cart Item Management:**  
   - Users can increase or decrease product quantities using the `handleQuantityChange` function, which updates the cart state.
   - The `handleDelete` function allows users to remove items from the cart.

5. **Expected Price Input:**  
   - Users can manually input an expected price for each product.

6. **Place Order:**  
   - The `handlePlaceOrder` function collects the necessary order information, formats it into a suitable payload, and sends it to the server using an API call (`/createQuotation`).  
   - If successful, a toast notification is shown, and the user is redirected to the product listing screen.

7. **Empty Cart State:**  
   - If the cart is empty, a placeholder animation is displayed along with a message.

---

#### **5. Profile Screen**  
The Profile Screen provides user information and access to loyalty points and allows for the option to log out from the app.

**Functions and Key Features:**  
1. **Customer Data Fetching:**  
   - Fetches customer details using `fetchCustomerDetailById` and updates the screen with loyalty points and user profile information.

2. **Display User Info:**  
   - Displays the user's profile picture and name, sourced from the Redux store's `loginUserData`.

3. **Loyalty Points:**  
   - Integrates a `LoyaltyCard` component that shows the customer’s current loyalty points.

4. **Redeem Loyalty Points:**  
   - The `handleRedeem` function checks if the user has enough loyalty points to redeem. If the user doesn’t meet the points threshold, a toast message is shown to inform them.

5. **Logout Functionality:**  
   - The `handleLogout` function clears the user’s session data from AsyncStorage and navigates them back to the login or splash screen, triggering a logout alert.

6. **Logout Confirmation Modal:**  
   - Displays a confirmation modal (`LogoutAlertModal`) to ensure users confirm their intent to log out.

## Options
### 1. **Product Details**

The **Product Details Screen** allows users to view detailed information about a specific product, including its name, category, stock status, pricing, and a description. Users can also add the product to their cart or place an order directly.


**Components:**

1. **TopNavHeader:**
   - Displays the title "Product Details" with a back navigation option.
   - Background color can be customized.

2. **Image:**
   - Displays the product image sourced from the provided URL.

3. **Text:**
   - Custom text component used to display product details such as name, category, cost, barcode, and description.

4. **Button:**
   - Triggers the action to add the product to the cart.

5. **OrderButton:**
   - Triggers the modal to order the product directly.

6. **OrderNowModal:**
   - Modal component that allows users to place an order for the product.

7. **View:**
   - Container for organizing layout and positioning of components.

---

### **Key Functions:**

1. **toggleModal:**
   - Toggles the visibility of the `OrderNowModal`.
   - **Usage:** Called when the user clicks the "Order Now" button.

2. **handleOrderNow:**
   - Opens the order modal for the product.
   - **Usage:** Triggered when the "Order Now" button is pressed.

3. **handleAddToCart:**
   - Dispatches an action to add the product to the Redux store's cart.
   - Shows a toast message indicating that the item has been added to the cart.
   - **Usage:** Triggered when the "Add to Cart" button is pressed.

4. **fetchData:**
   - Retrieves product details passed through navigation parameters.

---

### **Props:**

- **navigation:** Object containing navigation methods for screen transitions.
- **route:** Contains the product details passed from the previous screen.

---

### **State:**

- **isModalVisible:** Boolean state to control the visibility of the order modal.

---


### 2. Order Summary

The Order Summary screen provides users with a summary of the products they have selected for an order, allowing them to view product details, total price, and place an order.

---

#### Components Overview:
- **Header (TopNavHeader):** Displays the screen title ("Order Summary") with a back navigation option and a company logo image.
- **Product List (FlatList):** Displays a list of selected products with relevant details such as quantity, price, expected price, and category.
- **Total Price Section:** Displays the calculated total price for all selected products.
- **Action Buttons:**
  - **Add Products:** Navigates to the product selection screen.
  - **Place Order:** Initiates the order placement process.

---

#### Key Functions:

1. **useEffect (Calculate Total Price):**
   - **Purpose:** Automatically calculates the total price of selected products whenever there is a change in the selected product list.
   - **Process:** Iterates through selected products, summing up the `totalPrice` field.

2. **useEffect (Fetch Warehouse Data):**
   - **Purpose:** Fetches warehouse data from the server to associate with the order.
   - **Process:** Calls the `fetchWarehouse()` API and updates the `warehouse` state with the fetched data.

3. **handleDelete (Product Removal):**
   - **Purpose:** Removes a selected product from the list.
   - **Parameters:** `productId` – the ID of the product to remove.
   - **Process:** Dispatches the `removeSelectedProduct` action to update the product list in the Redux store.

4. **handlePlaceOrder (Place an Order):**
   - **Purpose:** Sends a request to create a new order with the selected products.
   - **Process:**
     - Maps the selected products to include necessary fields such as product ID, tax details, quantity, price, etc.
     - Prepares an order object (`productData`) with customer, warehouse, and product details.
     - Sends the order data via the `createQuotation` API request.
     - Displays a success or error message based on the response.
     - Clears the selected products from the cart upon successful order placement and navigates the user to the "Categories" screen.

---

#### UI Elements:

- **Product Container (FlatList Render Item):**
  - Displays each product's image, name, quantity, prices, and category.
  - Includes a delete button (`handleDelete`) to remove products from the list.
  
- **Total Price Container:** 
  - Displays the total calculated price based on the selected products.

- **Order Buttons:**
  - **Add Products:** Navigates the user to the product selection screen.
  - **Place Order:** Initiates the order process via the `handlePlaceOrder` function.

---

#### API Integration:
- **fetchWarehouse (Warehouse Fetch):** Fetches warehouse data to be used in order creation.
- **createQuotation (Order Placement):** Sends order details to the backend for processing.

---

#### State Management:
- **totalPrice:** Stores the total price of all selected products.
- **warehouse:** Stores the fetched warehouse information.
- **selectedProducts:** Retrieved from the Redux store, holds the list of products selected by the user.
  
---

#### Redux Actions:
- **removeSelectedProduct:** Removes a product from the selected products list.
- **clearSelectedProducts:** Clears all products from the cart after a successful order.

### 3. Product Enquiry

#### Purpose:
The Product Enquiry screen allows users to submit product inquiries by providing necessary details, including product information, customer details, and associated images. It captures user inputs and submits them to the server for further processing.

---

#### Components:
- **Header (TopNavHeader):** Displays the screen title ("Product Enquiry") with a back navigation option and a company logo image.
- **Input Fields:** Various fields for user input to gather necessary enquiry information.
- **Image Uploader:** Allows users to upload images related to the product inquiry.
- **Writing Pad (DrawingPad):** Provides a space for users to input additional product details through drawing.
- **Date Picker (DateTimePicker):** Allows users to select a date for the enquiry.
- **Submission Button (CustomButton):** Submits the enquiry details to the backend.

---

#### Key Functions:

1. **handleFieldChange:**
   - **Purpose:** Updates the state of `enquiryData` based on user input.
   - **Parameters:**
     - `field`: The field name to update.
     - `value`: The new value to set for the field.
   - **Process:** Uses `setEnquiryData` to update the corresponding field in the enquiry data object.

2. **handleEnquirySubmit:**
   - **Purpose:** Sends the filled enquiry form data to the server for processing.
   - **Process:**
     - Prepares the `enquiryFormData` object with necessary fields such as `date`, `submitted_by`, `product_detail`, etc.
     - Sends the data to the API endpoint (`/createProductEnquiryDetails`) using the `apiInstance`.
     - Displays a success message using `Toast` upon successful submission and navigates back to the previous screen.
     - Handles and logs errors if the submission fails.

---

#### UI Elements:

- **Input Fields:** 
  - **Select Date:** Allows users to pick a date for the enquiry.
  - **Product Name & Details:** Text input for entering product name and details.
  - **Customer Name & Number:** Text input for entering customer information.
  
- **Writing Pad (DrawingPad):** 
  - Allows users to provide additional details through freehand drawing.
  
- **Image Uploader (ImageUploader):** 
  - Enables users to upload images relevant to the product enquiry.

- **DateTimePicker:** 
  - Displays a date picker when the user taps on the date input field.

- **Submission Button:** 
  - Triggers the `handleEnquirySubmit` function to submit the enquiry data.

---

#### API Integration:
- **createProductEnquiryDetails (Enquiry Submission):** 
  - Sends enquiry details to the backend for processing, using a POST request with the populated `enquiryFormData`.

---

#### State Management:
- **scrollEnabled:** 
  - Manages whether the scroll view is enabled or not.
  
- **openDate:** 
  - Tracks whether the date picker is open.
  
- **imageUrl:** 
  - Stores the URL of the uploaded image.
  
- **enquiryData:** 
  - Contains the state of the enquiry form, including fields for selected date, product details, customer details, and a URL for the drawing pad.

---

#### Redux Actions:
- **useSelector:** 
  - Retrieves user data from the Redux store, specifically the `related_profile._id` for the user submitting the enquiry.

### 4. Feedback Screen 

The Feedback screen enables users to submit their feedback and complaints regarding services or products. It captures user inputs such as name, phone, email, emoji ratings, and detailed feedback along with optional image uploads.

---

#### Components:
- **Header (TopNavHeader):** Displays the screen title ("New Feedback/Complaint") with a back navigation option and a logo image.
- **Input Fields:** Collects user information, including name, phone, email, and feedback.
- **Emoji Rating:** Provides users with options to express their satisfaction level using emojis.
- **Image Uploader:** Allows users to upload images related to their feedback or complaint.
- **Writing Pad (DrawingPad):** Offers a space for users to add additional handwritten feedback.
- **Submission Button (CustomButton):** Triggers the submission of the feedback data to the backend.

---

#### Key Functions:

1. **handleFieldChange:**
   - **Purpose:** Updates the state of `feedbackFormData` based on user input.
   - **Parameters:**
     - `field`: The field name to update.
     - `value`: The new value to set for the field.
   - **Process:** Uses `setFeedbackFormData` to update the corresponding field in the feedback data object.

2. **handleEmojiPress:**
   - **Purpose:** Updates the selected emoji rating based on user interaction.
   - **Parameters:**
     - `rating`: The name of the emoji representing the user’s rating.
   - **Process:** Maps the selected emoji to its numeric value using `emojiRatingMapping` and updates the state with the selected rating.

3. **handleFeedbackSubmit:**
   - **Purpose:** Sends the filled feedback form data to the server for processing.
   - **Process:**
     - Prepares the `feedbackData` object with necessary fields including `date`, `customer_name`, `customer_mobile`, `customer_email`, and user rating.
     - Sends the data to the API endpoint (`/createComplaintAndFeedback`) using the `apiInstance`.
     - Displays a success message using `Toast` upon successful submission and navigates back to the previous screen.
     - Handles and logs errors if the submission fails.

---

#### UI Elements:

- **Input Fields:** 
  - **Customer Name:** Text input for entering the user’s name.
  - **Customer Phone:** Text input for entering the user’s phone number.
  - **Customer Email:** Text input for entering the user’s email address.
  
- **Emoji Rating:** 
  - Displays a selection of emojis representing different satisfaction levels. Users can select one to indicate their experience.
  
- **Writing Pad (DrawingPad):** 
  - Allows users to provide additional details through freehand drawing.

- **Feedback Input:**
  - A multi-line text input field for users to enter detailed feedback or complaints.

- **Image Uploader (ImageUploader):** 
  - Enables users to upload images relevant to their feedback.

- **Submission Button:** 
  - Triggers the `handleFeedbackSubmit` function to submit the feedback data.

---

#### API Integration:
- **createComplaintAndFeedback (Feedback Submission):** 
  - Sends feedback details to the backend for processing, using a POST request with the populated `feedbackData`.

---

#### State Management:
- **scrollEnabled:** 
  - Manages whether the scroll view is enabled or not.
  
- **imageUrl:** 
  - Stores the URL of the uploaded image.
  
- **feedbackFormData:** 
  - Contains the state of the feedback form, including fields for customer name, phone, email, complaints, and a URL for the drawing pad.
  
- **emojiRating:** 
  - Stores the numeric value of the selected emoji rating.

---

#### Redux Actions:
- **useSelector:** 
  - Retrieves user data from the Redux store, specifically the `related_profile._id` for the customer submitting feedback.

---

#### Styling:
- **Container:** 
  - The main container is styled with a background color and padding.
  
- **Scroll View:** 
  - Styled to provide a white background with rounded corners and padding for content display.

- **Emoji Container:**
  - Arranges emojis in a horizontal row, allowing users to select one easily.

- **Labels:**
  - Custom styles applied to labels for consistent font size and color.

- **Emoji Styles:**
  - Different styles for selected and unselected emojis to provide visual feedback on user selection.

