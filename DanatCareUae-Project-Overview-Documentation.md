### **DanatCareUae**

**DanatCareUae** is a customer-facing mobile application designed for product management and sales order quotation generation. The app focuses on enhancing the customer experience by providing features such as product search, quotation creation, category-wise product browsing, product enquiry, call, whatsapp connect, feedback and customer loyalty management.

---

### **Key Features:**

1. **Product Quotation Creation:**
   - Users can easily generate sales order quotations by selecting products and adding them to their cart. This feature is the core functionality of the app.
   
2. **Product Search and Listing:**
   - Users can search for products, with an option for category-based filtering, making product discovery faster and more intuitive.

3. **Cart Management:**
   - Products added to the cart are tracked for further action, such as creating a sales order quotation. The cart feature also supports dynamic updates and modifications.

4. **Customer Loyalty Points:**
   - The app integrates customer loyalty functionality, allowing users to view and manage loyalty points earned from purchases.

---

### **Project Structure Overview:**

The project structure consists of various directories and files necessary to maintain a clean and organized codebase.

```
├── App.js                # Main entry point of the app
├── assets/               # Contains image assets like logos, banners, and icons
├── src/                  # Source code directory containing main functionality
│   ├── api/              # API services and configurations
│   ├── components/       # Reusable UI components
│   ├── constants/        # App-wide constants such as colors and links
│   ├── navigation/       # Navigation setup for stack and tab-based navigation
│   ├── redux/            # Redux setup for state management
│   ├── screens/          # Screen components representing different views in the app
│   └── utils/            # Utility functions such as error handling
└── yarn.lock             # Yarn lock file for dependency management
```

---

### **Notable Directories and Files:**

1. **assets/**
   - Contains all images and media used in the app. 
   - Includes logos, loyalty card images, and various promotional banners.

2. **src/api/**
   - Houses API configuration and utility functions for making network requests.
   - Key files: `apiConfig.js`, `detailApi.js`, `uploadApi.js`.

3. **src/components/**
   - Contains reusable components such as buttons, modals, headers, and custom input fields.
   - Important components include `CustomButton.js`, `ModalCustomButton.js`, `ProductList.js`, and `LoyaltyCard.js`.

4. **src/screens/**
   - Contains all screen views of the app, including home, product categories, cart, orders, and profile pages.
   - Examples: `Cart.js`, `ProductDetails.js`, `OrderSummary.js`.

5. **src/redux/**
   - Manages global application state through actions and reducers.
   - Key files: `cartReducer.js`, `productAction.js`, `loginReducer.js`.

6. **src/navigation/**
   - Manages navigation between different screens via stack and tab navigators.
   - Files: `StackNavigator.js`, `TabNavigator.js`.

---

### **Core Functionalities:**

1. **Product Management:**
   - Search products, browse categories, and view product details.
   - Add products to the cart for quotation creation.

2. **Cart & Quotation Flow:**
   - Products added to the cart can be reviewed, modified, and converted into a sales order quotation.
   
3. **Loyalty Program:**
   - Displays customer loyalty points, allowing users to track rewards and redeem them.

4. **Sales Order Quotation:**
   - Primary purpose is generating and managing sales order quotations, aiding customers in making purchase decisions.

---
