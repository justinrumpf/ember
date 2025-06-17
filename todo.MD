# Ember POS Development Plan - Fresh Start

## 🎯 CURRENT STATUS (June 16, 2025)
**📋 STATUS**: Starting fresh development  
**🎨 APPROACH**: Expo Router file-based routing architecture (matching ImagineLabs project)  
**🎯 GOAL**: Build modern POS system with React Native and Node.js backend
**🔧 METHODOLOGY**: Incremental development with verification checkpoints
**📱 REFERENCE**: Use exact same stack as successful ImagineLabs project

---

## 📚 **EXACT STACK FROM IMAGINALABS PROJECT**

### **Frontend Dependencies (Match Exactly)**
```json
{
  "expo": "~53.0.11",
  "expo-router": "~5.1.0", 
  "react": "19.0.0",
  "react-native": "0.79.3",
  "typescript": "~5.8.3",
  "@expo/vector-icons": "^14.1.0",
  "@react-native-async-storage/async-storage": "2.1.2",
  "@react-navigation/native": "^7.1.6",
  "expo-auth-session": "~6.2.0",
  "expo-crypto": "~14.1.5",
  "expo-dev-client": "~5.2.0",
  "expo-font": "~13.3.1",
  "expo-linear-gradient": "^14.1.5",
  "expo-linking": "~7.1.5",
  "expo-splash-screen": "~0.30.9",
  "expo-status-bar": "~2.2.3",
  "expo-system-ui": "~5.0.8",
  "expo-web-browser": "~14.1.6",
  "react-native-gesture-handler": "~2.24.0",
  "react-native-reanimated": "~3.17.4",
  "react-native-safe-area-context": "5.4.0",
  "react-native-screens": "~4.11.1",
  "react-native-svg": "15.11.2"
}
```

### **Backend Dependencies (Match Exactly)**
```json
{
  "express": "^4.18.2",
  "mongoose": "^8.15.2",
  "jsonwebtoken": "^9.0.2",
  "bcryptjs": "^2.4.3",
  "cors": "^2.8.5",
  "dotenv": "^16.3.1",
  "express-rate-limit": "^7.1.5",
  "express-validator": "^7.0.1",
  "helmet": "^7.1.0"
}
```

### **Expo Configuration (app.json)**
```json
{
  "expo": {
    "newArchEnabled": true,
    "plugins": ["expo-router"],
    "experiments": {
      "typedRoutes": true
    }
  }
}
```

### **TypeScript Configuration**
```json
{
  "extends": "expo/tsconfig.base",
  "compilerOptions": {
    "strict": true,
    "paths": {
      "@/*": ["./*"]
    }
  }
}
```

---

## 🧪 **STEP-BY-STEP DEVELOPMENT PHILOSOPHY**

### **Why This Approach?**
- **🔍 VERIFY EARLY**: Catch issues when they're small and easy to fix
- **🏗️ BUILD SOLID**: Each layer depends on the previous working correctly  
- **⚡ MOVE FAST**: No time wasted on broken foundations
- **🎯 STAY FOCUSED**: Complete one thing fully before starting the next

### **How Each Step Works**
1. **Read the Goal**: Understand what we're building in this step
2. **Follow Substeps**: Complete each substep in order  
3. **Hit Checkpoint**: Verify the feature works as specified
4. **Fix Issues**: Don't proceed until checkpoint passes
5. **Move Forward**: Only then continue to next substep

### **Checkpoint Rules**
- **🛑 BLOCKING**: If checkpoint fails, stop and fix before continuing
- **✅ REQUIRED**: Every checkpoint must pass - no exceptions
- **📸 DOCUMENT**: Screenshot/demo each working checkpoint
- **🔄 ITERATE**: It's okay to go back and improve previous steps

---

## 🚨 IMMEDIATE PRIORITIES (First Development Session)

### **Priority 1: Project Foundation** 
**Goal**: Set up React Native project with Expo Router architecture

```typescript
// NEEDED: Expo Router project setup
// - TypeScript configuration
// - Professional folder structure
// - Modern file-based routing
```

**Action Items**:
1. Initialize React Native project with Expo Router
2. Set up TypeScript and development environment
3. Create professional folder structure
4. Configure Expo SDK and dependencies
5. Set up development workflow

### **Priority 2: Backend Foundation**
**Goal**: Create Node.js API with MongoDB integration

```typescript
// NEEDED: Complete backend API
// - Express server with TypeScript
// - MongoDB schemas and models
// - JWT authentication system
// - RESTful API endpoints
```

### **Priority 3: Authentication System**
**Goal**: Build secure login system connecting frontend to backend

---

## 📋 DEVELOPMENT PROMPT SEQUENCE WITH DETAILED SUBSTEPS

### **Prompt 1: Project Initialization**
**Goal**: Get basic Expo Router app running with TypeScript (EXACTLY like ImagineLabs)

#### **Step 1.1: Basic Expo Setup** ⚡ *VERIFY FIRST*
- Create new Expo project with EXACT same template as ImagineLabs
- Use Expo SDK ~53.0.11 and React Native 0.79.3
- Start development server and confirm app loads
- **✅ CHECKPOINT**: Basic app running on device/simulator (like ImagineLabs)

#### **Step 1.2: Expo Router Configuration** ⚡ *VERIFY BEFORE PROCEEDING*
- Install expo-router ~5.1.0 (exact version from ImagineLabs)
- Copy the EXACT file-based routing structure from ImagineLabs:
  ```
  app/
  ├── (tabs)/
  │   ├── _layout.tsx
  │   └── index.tsx
  ├── _layout.tsx
  ├── +not-found.tsx
  └── login.tsx
  ```
- Set up entry point: "main": "expo-router/entry" in package.json
- **✅ CHECKPOINT**: File-based routing working exactly like ImagineLabs

#### **Step 1.3: TypeScript Configuration** ⚡ *VERIFY TYPES WORKING*
- Copy EXACT tsconfig.json from ImagineLabs with strict mode
- Set up path aliases: "@/*": ["./*"] for absolute imports
- Install TypeScript ~5.8.3 (exact version from ImagineLabs)
- Add expo-env.d.ts file
- **✅ CHECKPOINT**: TypeScript compiling without errors, @/ imports working

#### **Step 1.4: Professional Setup Like ImagineLabs** ⚡ *VERIFY STRUCTURE*
- Copy the EXACT folder structure from ImagineLabs:
  ```
  ember-pos/
  ├── app/              # Expo Router pages
  ├── components/       # Reusable components
  ├── contexts/         # React contexts
  ├── constants/        # App constants
  ├── assets/          # Images, fonts, etc
  └── server/          # Backend (separate package.json)
  ```
- Set up app.json with newArchEnabled: true and typedRoutes: true
- Add the EXACT same EAS configuration from ImagineLabs
- **✅ CHECKPOINT**: Project structure matches ImagineLabs exactly

---

### **Prompt 2: MongoDB Schema Design**  
**Goal**: Design and document complete database schemas (NO CODE YET)

#### **Step 2.1: Core Entity Schemas** ⚡ *DESIGN ONLY*
- Design User/Employee schema with roles and permissions
- Design Store/Tenant schema for multi-tenant architecture
- Design basic Product/Inventory schema
- **✅ CHECKPOINT**: Core schemas documented with relationships

#### **Step 2.2: Transaction Schemas** ⚡ *DESIGN ONLY*
- Design Transaction/Sale schema with line items
- Design Payment schema with multiple payment types
- Design Customer schema with purchase history
- **✅ CHECKPOINT**: Transaction flow schemas complete

#### **Step 2.3: Advanced Feature Schemas** ⚡ *DESIGN ONLY*
- Design Consignment schema for consignment items
- Design Layaway schema for layaway transactions
- Design Reporting/Analytics schema for aggregated data
- **✅ CHECKPOINT**: All schemas documented, reviewed, and validated

---

### **Prompt 3: Node.js Backend Foundation**
**Goal**: Build working API with database connection (EXACTLY like ImagineLabs server)

#### **Step 3.1: Basic Express Setup** ⚡ *VERIFY SERVER STARTS*
- Create server/ directory with separate package.json
- Use EXACT Express setup from ImagineLabs with these dependencies:
  ```json
  {
    "express": "^4.18.2",
    "cors": "^2.8.5", 
    "helmet": "^7.1.0",
    "express-rate-limit": "^7.1.5",
    "express-validator": "^7.0.1",
    "dotenv": "^16.3.1"
  }
  ```
- Copy the EXACT middleware setup from ImagineLabs server.js
- **✅ CHECKPOINT**: Server starts on port 3000, responds to basic GET request

#### **Step 3.2: MongoDB Connection** ⚡ *VERIFY DATABASE CONNECTS*
- Use mongoose ^8.15.2 (exact version from ImagineLabs)
- Copy the EXACT connection setup from ImagineLabs
- Create test-connection.js script like ImagineLabs
- Set up MongoDB Atlas or local MongoDB
- **✅ CHECKPOINT**: Database connected, can save/retrieve test data

#### **Step 3.3: Authentication System** ⚡ *VERIFY AUTH WORKS*
- Use jsonwebtoken ^9.0.2 and bcryptjs ^2.4.3 (exact versions)
- Copy the EXACT JWT setup pattern from ImagineLabs
- Create login/logout endpoints matching ImagineLabs structure
- Add authentication middleware like ImagineLabs
- **✅ CHECKPOINT**: Can login, receive JWT, access protected routes

#### **Step 3.4: Core API Endpoints** ⚡ *VERIFY CRUD OPERATIONS*
- Copy the EXACT folder structure from ImagineLabs server:
  ```
  server/
  ├── config/          # Database config
  ├── middleware/      # Auth, validation middleware  
  ├── models/          # Mongoose schemas
  ├── package.json     # Backend dependencies
  ├── server.js        # Main server file
  └── .env             # Environment variables
  ```
- Create basic CRUD endpoints for Users and Products
- Use the EXACT error handling pattern from ImagineLabs
- **✅ CHECKPOINT**: All CRUD operations working via Postman/testing tool

---

### **Prompt 4: Authentication & Home Screen**
**Goal**: Connect frontend to backend authentication (EXACTLY like ImagineLabs pattern)

#### **Step 4.1: Authentication Context Setup** ⚡ *VERIFY CONTEXT WORKS*
- Copy the EXACT AuthContext pattern from ImagineLabs
- Create contexts/ directory and AuthContext.tsx
- Add useAuth hook with login/logout/user state
- Set up async-storage for token persistence
- **✅ CHECKPOINT**: AuthContext working, can login/logout in console

#### **Step 4.2: Layout and Navigation** ⚡ *VERIFY ROUTING PROTECTION*
- Copy the EXACT _layout.tsx structure from ImagineLabs
- Implement authentication guards and route protection
- Add LoadingScreen component like ImagineLabs
- Set up Stack navigation with proper screen options
- **✅ CHECKPOINT**: Auth guards working, redirects properly between login/main app

#### **Step 4.3: Login Screen** ⚡ *VERIFY LOGIN UI*
- Create login.tsx matching ImagineLabs structure
- Add form validation and error handling
- Connect to backend authentication API
- Add proper loading states and user feedback
- **✅ CHECKPOINT**: Complete login flow working end-to-end

#### **Step 4.4: Tab Navigation & Dashboard** ⚡ *VERIFY MAIN APP*
- Copy the EXACT (tabs)/_layout.tsx structure from ImagineLabs
- Create dashboard with POS-specific tabs (Sale, Inventory, Reports, etc.)
- Add proper tab icons and navigation
- Implement basic dashboard screen with sales summary
- **✅ CHECKPOINT**: Tab navigation working, dashboard accessible after login

---

### **Prompt 5: State Management & API Integration**
**Goal**: Add centralized state management (following ImagineLabs Context pattern)

#### **Step 5.1: Context Providers Setup** ⚡ *VERIFY CONTEXT WORKS*
- Copy the EXACT context provider pattern from ImagineLabs
- Create additional contexts for POS data (InventoryContext, TransactionContext)
- Set up context providers in root _layout.tsx like ImagineLabs
- Add proper TypeScript interfaces for all contexts
- **✅ CHECKPOINT**: Multiple contexts working, state shared across components

#### **Step 5.2: API Service Layer** ⚡ *VERIFY API INTEGRATION*
- Create centralized API service (lib/api.ts) for all backend calls
- Add JWT token handling and automatic refresh
- Implement error handling and retry logic
- Add offline detection and queue management
- **✅ CHECKPOINT**: All API calls centralized, token handling working

#### **Step 5.3: Data Fetching Hooks** ⚡ *VERIFY DATA LOADING*
- Create custom hooks for data fetching (useInventory, useTransactions)
- Add loading states, error handling, and caching
- Implement real-time updates for POS data
- Add data synchronization between frontend and backend
- **✅ CHECKPOINT**: Data fetching working, loading states smooth

#### **Step 5.4: Persistent State** ⚡ *VERIFY PERSISTENCE*
- Add AsyncStorage for offline data persistence
- Implement state hydration on app restart
- Add sync mechanism for offline-first functionality
- Test app restart and data persistence
- **✅ CHECKPOINT**: App state persists across restarts, offline functionality working

---

### **Prompt 6: Inventory Management**
**Goal**: Build complete inventory feature with backend integration

#### **Step 6.1: Inventory API Endpoints** ⚡ *VERIFY BACKEND FIRST*
- Expand inventory CRUD endpoints with search/pagination
- Add inventory category and supplier endpoints
- Test all endpoints with sample data
- **✅ CHECKPOINT**: Complete inventory API working with test data

#### **Step 6.2: Inventory List Screen** ⚡ *VERIFY UI WITH REAL DATA*
- Create inventory list screen with search and filters
- Connect to backend API using RTK Query
- Add pagination and loading states
- **✅ CHECKPOINT**: Inventory list showing real data from database

#### **Step 6.3: Inventory Details & Edit** ⚡ *VERIFY CRUD UI*
- Create inventory item detail screen
- Add edit/update functionality
- Implement image upload for products
- **✅ CHECKPOINT**: Can view, edit, and update inventory items

#### **Step 6.4: Barcode Scanning** ⚡ *VERIFY SCANNING WORKS*
- Add expo-camera for barcode scanning
- Implement barcode lookup functionality
- Add manual barcode entry fallback
- **✅ CHECKPOINT**: Barcode scanning working, can look up products

#### **Step 6.5: Add New Inventory** ⚡ *VERIFY CREATION FLOW*
- Create add new inventory item screen
- Add form validation and image upload
- Test complete create flow with real data
- **✅ CHECKPOINT**: Can create new inventory items end-to-end

---

### **Prompt 7: Sales Transaction Screen**
**Goal**: Build complete POS transaction system

#### **Step 7.1: Transaction API** ⚡ *VERIFY BACKEND FIRST*
- Create transaction endpoints (create, retrieve, update)
- Add transaction line item management
- Implement inventory quantity updates on sale
- **✅ CHECKPOINT**: Transaction API working with inventory updates

#### **Step 7.2: Item Search & Selection** ⚡ *VERIFY ITEM LOOKUP*
- Create item search interface for POS
- Add barcode scanning integration
- Implement quick item selection
- **✅ CHECKPOINT**: Can search and select items for sale

#### **Step 7.3: Shopping Cart Management** ⚡ *VERIFY CART OPERATIONS*
- Build shopping cart with add/remove/quantity changes
- Calculate totals including tax
- Add discount application
- **✅ CHECKPOINT**: Shopping cart fully functional with calculations

#### **Step 7.4: Payment Processing** ⚡ *VERIFY PAYMENT FLOW*
- Create payment screen with multiple payment types
- Add cash, card, and split payment options
- Implement change calculation
- **✅ CHECKPOINT**: Payment processing working, transactions complete

#### **Step 7.5: Receipt Generation** ⚡ *VERIFY RECEIPT OUTPUT*
- Create receipt preview and print functionality
- Add email receipt option
- Store transaction records properly
- **✅ CHECKPOINT**: Complete transaction with receipt generation

---

### **Prompt 8: Customer Management**
**Goal**: Add customer features and transaction history

#### **Step 8.1: Customer API** ⚡ *VERIFY BACKEND FIRST*
- Create customer CRUD endpoints
- Add customer search and lookup
- Link customers to transactions
- **✅ CHECKPOINT**: Customer API working with transaction linking

#### **Step 8.2: Customer Lookup/Creation** ⚡ *VERIFY CUSTOMER UI*
- Add customer search during checkout
- Create new customer registration
- Link customers to transactions
- **✅ CHECKPOINT**: Customer lookup and creation working in POS

#### **Step 8.3: Customer Purchase History** ⚡ *VERIFY HISTORY DISPLAY*
- Create customer profile screen
- Display purchase history and totals
- Add customer transaction search
- **✅ CHECKPOINT**: Customer history and profiles working

---

### **Prompt 9: Reporting & Analytics**
**Goal**: Build reporting system with real data

#### **Step 9.1: Reporting API** ⚡ *VERIFY DATA AGGREGATION*
- Create sales report endpoints with date ranges
- Add inventory report endpoints
- Implement employee performance reports
- **✅ CHECKPOINT**: Reporting API returning accurate aggregated data

#### **Step 9.2: Sales Reports UI** ⚡ *VERIFY REPORT DISPLAY*
- Create sales report screens with charts
- Add date range selection and filters
- Implement report export functionality
- **✅ CHECKPOINT**: Sales reports displaying with visual charts

#### **Step 9.3: Inventory Reports** ⚡ *VERIFY INVENTORY ANALYTICS*
- Create inventory level reports
- Add low stock alerts and notifications
- Implement product performance analytics
- **✅ CHECKPOINT**: Inventory reports helping with stock management

---

### **Prompt 10: Advanced Features**
**Goal**: Add advanced POS functionality

#### **Step 10.1: Advanced Payment Processing** ⚡ *VERIFY COMPLEX PAYMENTS*
- Add layaway payment functionality
- Implement returns and exchanges
- Add store credit and gift card support
- **✅ CHECKPOINT**: Advanced payment options working

#### **Step 10.2: Discount & Promotion System** ⚡ *VERIFY PROMOTIONS*
- Create discount management system
- Add promotion codes and automatic discounts
- Implement loyalty program integration
- **✅ CHECKPOINT**: Discount system working in transactions

#### **Step 10.3: Multi-Store & User Management** ⚡ *VERIFY MULTI-TENANT*
- Add store/location management
- Implement user role and permission system
- Add inter-store inventory transfers
- **✅ CHECKPOINT**: Multi-store functionality working with proper access control

---

## 🏗️ **ARCHITECTURAL DECISIONS TO MAKE**

### **Frontend Framework Choice**
- **OPTION 1**: Expo Router (file-based routing)
- **OPTION 2**: React Navigation (traditional navigation)
- **DECISION NEEDED**: Which approach for navigation?

### **State Management**
- **OPTION 1**: Redux Toolkit with RTK Query
- **OPTION 2**: Context API with React Query
- **DECISION NEEDED**: State management strategy?

### **Backend Architecture**
- **OPTION 1**: Monolithic Express API
- **OPTION 2**: Microservices architecture
- **DECISION NEEDED**: Backend structure approach?

### **Database Strategy**
- **OPTION 1**: MongoDB with Mongoose
- **OPTION 2**: PostgreSQL with Prisma
- **DECISION NEEDED**: Database and ORM choice?

---

## 🎯 **SUCCESS METRICS & VERIFICATION CHECKPOINTS**

### **Verification Philosophy** 
**🔍 RULE**: Each checkpoint must pass before proceeding to next step
**⚡ TESTING**: Every substep includes a specific verification checkpoint
**🛑 BLOCKING**: If checkpoint fails, fix before continuing

### **Step-by-Step Verification Guide**

#### **For Frontend Steps**
- **UI Verification**: Screenshot/video of working interface
- **Navigation Verification**: Can navigate between all screens
- **Data Verification**: Real data displaying correctly from API
- **Performance Verification**: Smooth interactions, no lag

#### **For Backend Steps**  
- **API Verification**: Test with Postman/Insomnia
- **Database Verification**: Data persisting correctly in MongoDB
- **Authentication Verification**: JWT tokens working properly
- **Error Handling Verification**: Proper error responses

#### **For Integration Steps**
- **End-to-End Verification**: Complete user workflow testing
- **Real Data Verification**: Using actual POS scenarios, not mock data
- **Error Recovery Verification**: Graceful handling of failures
- **Performance Verification**: Acceptable response times under load

### **Critical Checkpoints That Block Progress**

#### **🚨 Checkpoint 1.2**: Expo Router must work before any UI development
#### **🚨 Checkpoint 3.2**: Database connection must work before API development  
#### **🚨 Checkpoint 4.3**: Authentication must work before protected features
#### **🚨 Checkpoint 5.2**: Redux state must work before complex features
#### **🚨 Checkpoint 6.1**: Inventory API must work before inventory UI
#### **🚨 Checkpoint 7.1**: Transaction API must work before POS screens

---

## 📝 **VERIFICATION CHECKLIST TEMPLATE**

### **After Each Substep, Verify:**
```
□ Code compiles without TypeScript errors
□ App/server starts without warnings  
□ Feature works as demonstrated in checkpoint
□ No console errors or warnings
□ Meets performance expectations
□ Code is properly documented and clean
```

### **Before Moving to Next Prompt:**
```
□ All substeps completed and verified
□ Full feature testing completed
□ Integration testing passed
□ Code reviewed and refactored if needed
□ Documentation updated
□ Ready for next development phase
```

---

## 📚 **EXACT CODE ORGANIZATION (Matching ImagineLabs)**

### **Frontend Structure (EXACT ImagineLabs Pattern)**
```
ember-pos/
├── app/                    # Expo Router pages (EXACT like ImagineLabs)
│   ├── (tabs)/            # Tab navigation group
│   │   ├── _layout.tsx    # Tab layout configuration
│   │   ├── index.tsx      # Dashboard/home tab
│   │   ├── sale.tsx       # POS transaction tab
│   │   ├── inventory.tsx  # Inventory management tab
│   │   └── reports.tsx    # Reports and analytics tab
│   ├── _layout.tsx        # Root layout with providers
│   ├── +not-found.tsx     # 404 page
│   ├── login.tsx          # Authentication screen
│   ├── settings.tsx       # Settings screen
│   └── modal.tsx          # Modal screens
├── components/            # Reusable UI components
├── contexts/              # React Context providers (like ImagineLabs)
│   ├── AuthContext.tsx    # Authentication state
│   ├── InventoryContext.tsx # Inventory management
│   └── TransactionContext.tsx # POS transactions
├── constants/             # App constants and configuration
├── lib/                   # Utility functions and API client
├── assets/               # Images, fonts, icons
│   ├── images/           # App images
│   └── fonts/            # Custom fonts
├── app.json              # Expo configuration (EXACT like ImagineLabs)
├── eas.json              # EAS build configuration
├── tsconfig.json         # TypeScript config (EXACT like ImagineLabs)
├── expo-env.d.ts         # Expo TypeScript declarations
└── package.json          # Frontend dependencies
```

### **Backend Structure (EXACT ImagineLabs Server Pattern)**
```
server/
├── config/               # Database and app configuration
│   └── database.js       # MongoDB connection setup
├── middleware/           # Express middleware
│   ├── auth.js          # JWT authentication middleware
│   ├── validation.js    # Request validation
│   └── rateLimiting.js  # Rate limiting
├── models/              # Mongoose schemas
│   ├── User.js          # Employee/user model
│   ├── Product.js       # Inventory/product model
│   ├── Transaction.js   # Sales transaction model
│   └── Customer.js      # Customer model
├── routes/              # API endpoints
│   ├── auth.js          # Authentication routes
│   ├── inventory.js     # Inventory management
│   ├── transactions.js  # POS transaction routes
│   └── reports.js       # Reporting endpoints
├── .env                 # Environment variables
├── server.js           # Main server file (EXACT like ImagineLabs)
├── test-connection.js  # Database connection test
└── package.json        # Backend dependencies (EXACT versions)
```

### **API Service Layer (ImagineLabs Pattern)**
```typescript
// lib/api.ts - Centralized API client (like ImagineLabs)
// contexts/AuthContext.tsx - Authentication state management
// contexts/InventoryContext.tsx - Inventory data management
// contexts/TransactionContext.tsx - POS transaction management
```

---

## 🚀 **DEVELOPMENT SETUP REQUIREMENTS**

### **Environment Setup**
```bash
# Required Tools:
# - Node.js 18+
# - MongoDB or MongoDB Atlas
# - Expo CLI
# - TypeScript
# - VS Code with React Native extensions
```

### **Project Structure**
```
ember-pos/
├── frontend/        # React Native Expo app
├── backend/         # Node.js API server
├── shared/          # Shared types and utilities
└── docs/           # Documentation
```

### **Development Workflow**
1. **Setup**: Initialize both frontend and backend projects
2. **Backend First**: Build API and database schemas
3. **Frontend Integration**: Connect UI to backend services
4. **Testing**: Unit, integration, and E2E testing
5. **Deployment**: Production deployment configuration

---

## 💡 **DEVELOPMENT PRINCIPLES**

### **Code Quality**
- TypeScript throughout the entire stack
- Comprehensive error handling and validation
- Clean architecture with separation of concerns
- Consistent code formatting and linting

### **User Experience**
- Fast and responsive interface
- Intuitive navigation and workflows
- Offline-first architecture
- Professional POS aesthetics

### **Scalability**
- Multi-tenant architecture support
- Efficient database queries and indexing
- Modular component design
- Performance monitoring and optimization

### **Security**
- Secure authentication and authorization
- Data encryption and validation
- API rate limiting and protection
- Audit logging for all transactions

---

## 🚀 **IMMEDIATE NEXT STEPS - QUICK REFERENCE (ImagineLabs Setup)**

### **Right Now: Start with Prompt 1, Step 1.1 (EXACT ImagineLabs Setup)**
```bash
# FIRST ACTION: Create Expo app with EXACT same setup as ImagineLabs
npx create-expo-app ember-pos --template blank-typescript

cd ember-pos

# Install EXACT same Expo Router version as ImagineLabs
npx expo install expo-router@~5.1.0

# Set main entry point (EXACT same as ImagineLabs)
# Edit package.json: "main": "expo-router/entry"

# Install EXACT dependency versions from ImagineLabs
npx expo install expo@~53.0.11 react@19.0.0 react-native@0.79.3

# VERIFY: App starts and shows basic screen
npx expo start --port 8085

# CHECKPOINT 1.1: ✅ Basic app running EXACTLY like ImagineLabs before proceeding
```

### **Copy Exact Configuration Files from ImagineLabs**
```bash
# After basic setup, copy these EXACT files from ImagineLabs:
# - app.json (with newArchEnabled: true, typedRoutes: true)
# - tsconfig.json (with strict mode and @/* paths)
# - eas.json (EAS build configuration)
# - expo-env.d.ts (TypeScript declarations)
```

### **Development Order (NEVER Skip Steps - Follow ImagineLabs Pattern)**
1. **Step 1.1** → Basic Expo app working (exact ImagineLabs setup)
2. **Step 1.2** → Expo Router navigation working (copy ImagineLabs structure)
3. **Step 1.3** → TypeScript compiling cleanly (copy ImagineLabs tsconfig.json)
4. **Step 1.4** → Folder structure organized (copy ImagineLabs structure)
5. **Step 2.1** → Database schemas designed
6. **Step 3.1** → Backend setup (copy ImagineLabs server structure)
7. **Continue...** → Following the detailed substeps with ImagineLabs patterns

### **Key Reminders for ImagineLabs Compatibility**
- **🔍 COPY EXACT VERSIONS**: Use exact same package versions as ImagineLabs
- **📁 COPY EXACT STRUCTURE**: Use same folder organization as ImagineLabs  
- **⚙️ COPY EXACT CONFIG**: Use same app.json, tsconfig.json settings
- **🎨 COPY EXACT PATTERNS**: Use same Context providers, authentication flow
- **🛑 STOP IF DIFFERENT**: If setup differs from ImagineLabs, fix immediately
- **📸 DOCUMENT**: Screenshot each working checkpoint for reference
- **💾 COMMIT OFTEN**: Git commit after each successful checkpoint

---

**🎯 READY TO START: Prompt 1, Step 1.1 - EXACT ImagineLabs Setup**  
**📍 Next Action**: Create Expo project with ImagineLabs configuration  
**🎨 Focus**: Mirror the working ImagineLabs setup exactly**
