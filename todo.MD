help me come up with a set of AI prompts to create a POS system in react native. The POS system will be codenamed "Ember".
I want the POS system to be designed for a resale/consignment/layaway store with these specialized inventory purchase features. 

This app will need to run in React Native on iOS. I will use Expo.dev also. 

You will follow these general guidelines:

1. After each implementation, test thoroughly before moving to the next
2. Modify these prompts based on specific business rules discovered during development
5. Keep the MongoDB schema flexible to accommodate future changes
6. Maintain a comprehensive test suite as you build

Perform each step below. After each step has been completed, commit the change to github. Also create a tracking MD document where you can 
track what steps in this document have been completed. This will be useful so subsequent chats can pick up where we leave off in a previous chat. 

The github project is located here: https://github.com/justinrumpf/ember.git

## Phase 1: Foundation & Setup

### Prompt 1: Project Initialization
```
Create a new React Native project with TypeScript support for a POS system that will run on both tablets and phones. Set up the following:
1. React Native project with TypeScript
2. Navigation structure using React Navigation with drawer navigation for main menu and stack navigation for screens
3. Redux Toolkit for state management with offline persistence using redux-persist
4. Basic folder structure: /src/components, /src/screens, /src/store, /src/services, /src/models, /src/utils
5. Configure react-native-vector-icons for UI icons
6. Set up environment variables for API endpoints
Include basic App.tsx with navigation setup.
```

### Prompt 2: MongoDB Schema Design
```
Based on these MSSQL tables, create MongoDB schemas using Mongoose for a Node.js backend. Convert the following SQL tables to MongoDB collections with appropriate relationships:
- vendors (from vendor.sql) - for customers/consignors
- inventory (from invhdr.sql) - main inventory items
- transactions (from poslog.sql) - transaction log
- employees (from salesper.sql) - employee/salesperson data. a salesperson/employee can be a part of multiple stores and even multiple tenancies. 
- registers (from registex.sql) - register/terminal info
- styles, sizes, colors, brands, departments, categories (from respective SQL files)
- configuration (from ctrlgenl.sql and ctrlps.sql) - store configuration
- tenancy - tables to manage multi-tenant. 
- stores - table to manage which stores are part of which tenancy. Each tenant can have multiple stores attached to it. 
- concept - a tenancy can contain multiple different types of stores, each brand called a concept. 
- franchise - this structure sits about the tenancy table. We will have users a part of the corporate franchise company that need access to all users/tenants within that franchise code. 

We also need to have tech users that can access any franchise, tenancy, store, etc. God mode. 

Include subdocuments where appropriate and maintain referential integrity. Add fields for:
- consignment tracking (consignor_id, split_percentage, consignment_end_date)
- layaway tracking (customer_id, deposit, payment_schedule, status)
- multi-location support (location_id references)
```

### Prompt 3: Node.js Backend Foundation
```
Create a Node.js Express server with the following:
1. Express setup with TypeScript
2. MongoDB connection using Mongoose
3. JWT authentication for employees
4. RESTful API structure with routes for:
   - /api/auth (login, logout, refresh)
   - /api/inventory (CRUD operations)
   - /api/transactions (create, read, void)
   - /api/vendors (customers/consignors CRUD)
   - /api/employees (CRUD with role management)
   - /api/config (store configuration)
5. Middleware for authentication, error handling, and request logging
6. Socket.io setup for real-time updates between devices
Include offline queue mechanism for syncing when connection restored.
```

## Phase 2: Core POS Features

### Prompt 4: Authentication & Home Screen
```
Create React Native screens for:
1. Login screen with employee code/password or PIN entry
2. Fingerprint authentication option (using react-native-biometrics)
3. Home dashboard showing:
   - Today's sales summary
   - Active register info
   - Quick action buttons (New Sale, New Buy, Lookup, Reports)
   - Notification badges for pending layaways/consignments
4. Drawer menu with navigation to all major functions
5. Store employee info in Redux with role-based access control
Include offline login capability using cached credentials.
```

### Prompt 5: Inventory Management Screen
```
Create an inventory management system with:
1. Barcode scanning using react-native-camera
2. Manual SKU entry with autocomplete
3. Inventory item creation form with:
   - All fields from the invhdr table
   - Style/Size/Color/Brand selection with ability to add new
   - Department/Category hierarchical selection
   - Multiple pricing tiers (A-F from styles.sql)
   - Consignment fields (vendor, split %, end date)
   - Photo capture for items
4. Inventory search/filter screen
5. Quick inventory lookup by scan
6. Offline storage of inventory in Redux persist
Include dynamic pricing calculation based on style factors and conditions.
```

### Prompt 6: Sales Transaction Screen
```
Build a comprehensive sales transaction screen:
1. Item entry via barcode scan or manual search
2. Shopping cart with line items showing:
   - Item details (style, size, color, brand)
   - Original price and any discounts
   - Running total with tax calculation
3. Customer selection/creation with search
4. Discount application (from discount.sql types)
5. Multiple payment methods in single transaction:
   - Cash (with change calculation)
   - Credit/Debit (REST API integration placeholder)
   - Check
   - Store Credit
   - Gift Card
6. Receipt preview and printing/email options
7. Transaction suspension and recall
Include offline transaction queuing with unique transaction IDs.
```

## Phase 3: Specialized Features

### Prompt 7: Buy/Purchase Transaction Screen
```
Create a buying interface for purchasing inventory:
1. Vendor/Consignor selection or creation
2. Bulk item entry with:
   - Barcode generation for items without
   - Batch style/brand assignment
   - Automatic pricing based on condition and factors
   - Consignment split configuration per vendor or per item
3. Payment methods:
   - Cash (with configurable limits)
   - Check
   - Store Credit
   - Trade-in credit
4. Multiple purchase types in one transaction:
   - Outright purchase
   - Consignment
   - Trade-in (generate credit)
5. Print/email receipts with terms
6. Automatic inventory creation
Include proper cost tracking and profit margin calculations.
```

### Prompt 8: Layaway Management
```
Build a complete layaway system:
1. Layaway creation from sales screen with:
   - Configurable deposit percentage (default 20%)
   - Payment schedule generation
   - Fee structure (configurable)
   - Terms & conditions display
2. Layaway lookup screen by:
   - Customer name/phone
   - Layaway number
   - Item description
3. Payment collection screen
4. Layaway cancellation with:
   - Configurable restocking fee
   - Refund calculation
   - Return items to inventory
5. Overdue layaway notifications
6. Layaway aging report
Store layaway data with status tracking and payment history.
```

### Prompt 9: Consignment Management
```
Create consignment tracking features:
1. Consignor portal showing:
   - Active inventory
   - Sold items pending payout
   - Payment history
   - Agreement terms
2. Automatic markdown scheduling:
   - 30/60/90 day markdowns (configurable)
   - Percentage or fixed amount reductions
3. End-of-consignment processing:
   - Recall items for pickup
   - Convert to store inventory (buy out)
   - Donation option with tracking
4. Payout calculation and processing:
   - Batch payout by date range
   - Individual consignor payout
   - Check/cash/store credit options
5. Consignment agreement printing
Include aging reports and automated notifications.
```

## Phase 4: Payment & Hardware Integration

### Prompt 10: Payment Processing Integration
```
Implement payment processing features:
1. REST API integration structure for credit/debit:
   - Configurable endpoint URLs
   - Transaction request/response handling
   - Timeout and retry logic
   - Offline transaction storage
2. Signature capture for credit transactions
3. Receipt configuration based on payment type
4. Cash drawer control integration
5. Check verification workflow
6. Gift card/store credit:
   - Issue new cards/credits
   - Balance lookup
   - Partial redemption
   - Transaction history
7. Payment reconciliation screen
Include EMV compliance fields and PCI consideration comments.
```

### Prompt 11: Barcode & Printing Integration
```
Add hardware integration features:
1. Barcode/QR code generation:
   - Custom SKU format with location/date encoding
   - Bulk printing interface
   - Label size templates (from MSSQL labeltype)
2. Barcode scanning with:
   - Camera-based scanning (react-native-camera)
   - External scanner support via keyboard wedge
   - Scan history and error handling
3. Receipt printing:
   - Bluetooth printer support (react-native-bluetooth-escpos-printer)
   - Network printer support
   - Receipt template customization
   - Email receipt option
4. Report printing functionality
5. Price tag/label printing
Include offline print queue and printer status monitoring.
```

## Phase 5: Reporting & Administration

### Prompt 12: Daily Operations & Reports
```
Create daily operation screens:
1. Register open/close with:
   - Starting cash entry
   - Blind close option
   - Cash reconciliation
   - Deposit preparation
2. Daily reports including:
   - Sales summary by department/category
   - Payment method breakdown
   - Employee performance
   - Hourly sales analysis
3. Inventory reports:
   - Aging analysis
   - Slow-moving items
   - Consignment expiration
   - Stock levels by category
4. Financial reports:
   - Profit margins
   - Tax collected
   - Payout obligations
5. Export functionality (CSV/PDF)
Include drill-down capabilities and date range selection.
```

### Prompt 13: Multi-location & Sync
```
Implement multi-location support:
1. Location selection on login
2. Inventory transfers between locations:
   - Transfer request/approval workflow
   - In-transit tracking
   - Auto-receive or manual confirmation
3. Cross-location inventory lookup
4. Consolidated reporting across locations
5. Real-time sync using Socket.io:
   - Inventory updates
   - Price changes
   - Transaction notifications
6. Conflict resolution for offline changes
7. Location-specific configuration:
   - Tax rates
   - Receipt messages
   - Pricing rules
Include role-based access to location data.
```

### Prompt 14: Employee & Commission Management
```
Build employee management features:
1. Employee profile management:
   - Roles and permissions
   - Commission rates by category/type
   - Schedule tracking
   - Performance goals
2. Commission calculation:
   - Sale-based commissions
   - Buyer incentives
   - Split commissions
   - Spiffs and bonuses
3. Time clock functionality:
   - Clock in/out
   - Break tracking
   - Overtime calculation
4. Employee sales report
5. Commission payout report
6. Access level management by screen/function
Include audit trail for all employee actions.
```

## Phase 6: Advanced Features & Polish

### Prompt 15: Customer Management & Loyalty
```
Create comprehensive customer features:
1. Customer profile with:
   - Purchase history
   - Preferences (sizes, brands, styles)
   - Contact preferences (email/SMS)
   - Tax exemption support
2. Customer search and merge duplicates
3. Marketing opt-in/out management
4. Purchase analytics per customer:
   - Lifetime value
   - Average transaction
   - Preferred categories
5. Automated notifications:
   - New arrivals matching preferences
   - Layaway payment reminders
   - Birthday rewards
6. Loyalty program (optional):
   - Points earning/redemption
   - Tier benefits
   - Special pricing
Include GDPR compliance features and data export.
```

### Prompt 16: Configuration & Settings
```
Build a comprehensive settings module:
1. Store configuration:
   - Basic info (name, address, phone)
   - Tax rates and rules
   - Receipt messages
   - Business hours
2. Pricing configuration:
   - Markup matrices
   - Rounding rules
   - Discount limits
   - Automatic markdown rules
3. Hardware settings:
   - Printer configuration
   - Scanner settings
   - Cash drawer setup
   - Card reader configuration
4. Feature toggles:
   - Consignment on/off
   - Layaway on/off
   - Trade-ins on/off
   - Commission tracking
5. Backup and restore
6. Data export/import tools
Include change logging and permission requirements.
```

### Prompt 17: Performance & Polish
```
Optimize the application with:
1. Performance improvements:
   - Lazy loading for screens
   - Image optimization and caching
   - Database query optimization
   - Pagination for large lists
2. UI/UX enhancements:
   - Loading states and skeletons
   - Error boundaries and fallbacks
   - Swipe gestures for common actions
   - Keyboard shortcuts for desktop
3. Search optimization:
   - Full-text search implementation
   - Search suggestions
   - Recent searches
   - Filter preservation
4. Data validation:
   - Form validation rules
   - Business logic validation
   - Duplicate prevention
5. Help system:
   - In-app tutorials
   - Context-sensitive help
   - FAQ section
Include crash reporting and analytics integration.
```

