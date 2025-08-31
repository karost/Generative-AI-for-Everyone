
I have audited the previous implement.md file draft for correctness, completeness, clarity, and best practices for AI-driven code generation workflows, especially with modern tech stacks and incremental testing. Here is the updated and fully refined implement.md, considering:

- Modern stack: frontend fully separated as Next.js & Tailwind CSS, backend as standalone Node.js Fastify API server with ES modules.
- All tasks broken into focused steps with clear AI prompts.
- Each task includes self-test instructions for AI to validate working code increments.
- Clear project separation with frontend/backend architecture.
- Organized and readable markdown structure using best markdown documentation practices.
- No extraneous commentary, just precise instructions for AI and developers.

***

# implement.md

## Phase 1: Backend Setup and API Design

### Task 1.1: Initialize Backend Project with Fastify
- **Description:** Setup Node.js backend using Fastify with ES modules, CORS, and dotenv.
- **Steps:**
  1. Initialize new Node.js project with `"type": "module"`.
  2. Install Fastify, `@fastify/cors`, `dotenv`.
  3. Create `server.js` to:
     - Import Fastify.
     - Register CORS.
     - Load environment variables.
     - Listen on port 4000.
     - Add GET `/api/health` returning `{ status: 'ok' }`.
- **AI Sub-prompt:**
  ```
  Generate Fastify backend setup with ES modules. Include CORS and dotenv. Create server.js with health check `/api/health` returning status ok. Listen on port 4000.
  ```
- **Self-test:**
  - Call GET `/api/health` → response `{ status: 'ok' }`.
  - Confirm server startup logs appear.

***

### Task 1.2: Define MongoDB Schemas for Product and User
- **Description:** Setup Mongoose with environment config and define Product & User models.
- **Steps:**
  1. Connect to MongoDB with Mongoose using env vars.
  2. Create `models/Product.js` with: `name` (string), `description` (string), `price` (number), `imageUrl` (string).
  3. Create `models/User.js` with: `username` (string), `email` (string), `password` (hashed string).
- **AI Sub-prompt:**
  ```
  Generate ES modules Mongoose schemas/models for Product (name, description, price, imageUrl) and User (username, email, hashed password).
  ```
- **Self-test:**
  - Write small scripts to create and retrieve a Product and a User.
  - Log results verifying DB operations.

***

### Task 1.3: Implement Product REST API Endpoints
- **Description:** Create REST routes for product CRUD operations.
- **Steps:**
  1. GET `/api/products` → list all products.
  2. POST `/api/products` → add new products.
  3. GET `/api/products/:id` → get product details by ID.
- **AI Sub-prompt:**
  ```
  Generate Fastify routes for products: GET /api/products, POST /api/products, GET /api/products/:id. Use Mongoose for DB operations, include error handling.
  ```
- **Self-test:**
  - GET products returns array.
  - POST adds product returns success.
  - GET product by ID returns correct info.

***

### Task 1.4: User Authentication with JWT
- **Description:** Build secure user register and login endpoints with bcrypt and JWT.
- **Steps:**
  1. POST `/api/users/register` hashes password before saving.
  2. POST `/api/users/login` verifies and returns JWT.
- **AI Sub-prompt:**
  ```
  Generate Fastify routes for POST /api/users/register and /login using bcrypt for password hashing and JWT for tokens.
  ```
- **Self-test:**
  - Register new user success.
  - Login yields JWT token.

***

### Task 1.5: Cart and Order API Implementation
- **Description:** Create authenticated routes for cart management and orders.
- **Steps:**
  1. POST `/api/cart` add/update cart items.
  2. GET `/api/cart` retrieve cart items.
  3. POST `/api/orders` submit order based on cart.
- **AI Sub-prompt:**
  ```
  Generate Fastify routes for authenticated POST /api/cart, GET /api/cart, POST /api/orders using JWT authentication.
  ```
- **Self-test:**
  - Authenticated operations succeed.
  - Unauthorized access blocked.

***

## Phase 2: Frontend Setup and Development (Next.js + Tailwind CSS)

### Task 2.1: Setup Next.js Project with Tailwind CSS
- **Description:** Bootstrap Next.js app and configure Tailwind CSS.
- **Steps:**
  1. Create Next.js project.
  2. Install and configure Tailwind CSS.
  3. Add base layout and global styles.
- **AI Sub-prompt:**
  ```
  Generate Next.js app with Tailwind CSS integration. Setup global styles and layout.
  ```
- **Self-test:**
  - Run Next.js dev server.
  - Verify Tailwind styles apply.

***

### Task 2.2: Product Listing Page
- **Description:** Fetch products via API and display in grid.
- **Steps:**
  1. Create `/pages/index.js`.
  2. Fetch `/api/products` backend endpoint.
  3. Display product cards with image, name, price.
- **AI Sub-prompt:**
  ```
  Generate Next.js /pages/index.js that fetches products from backend and displays them responsively with Tailwind CSS.
  ```
- **Self-test:**
  - Products load and render correctly.
  - Network fetch status is 200.

***

### Task 2.3: Product Detail Page with Add to Cart
- **Description:** Dynamic product page with detail view and Add to Cart.
- **Steps:**
  1. Create `/pages/products/[id].js`.
  2. Fetch product details from backend.
  3. Add button to add product to cart state.
- **AI Sub-prompt:**
  ```
  Generate dynamic Next.js product details page with Add to Cart button using Tailwind styles.
  ```
- **Self-test:**
  - Detail data loads.
  - Add to Cart updates state.

***

### Task 2.4: Cart State Management and Page
- **Description:** Manage cart globally and display cart page.
- **Steps:**
  1. Use React Context or Zustand for cart state.
  2. Create `/pages/cart.js` displaying items and remove option.
- **AI Sub-prompt:**
  ```
  Generate React cart state management using Context or Zustand and /cart page UI allowing remove items.
  ```
- **Self-test:**
  - Cart state persists.
  - Items add/remove correctly.

***

### Task 2.5: User Auth Forms and Integration
- **Description:** Create login/register UI pages linked to backend auth.
- **Steps:**
  1. Create `/pages/login.js` and `/pages/register.js` with forms.
  2. Call backend auth endpoints.
  3. Store JWT in HttpOnly cookie or localStorage.
- **AI Sub-prompt:**
  ```
  Generate Next.js login and registration forms that authenticate against backend and store JWT securely.
  ```
- **Self-test:**
  - Successful login/register returns JWT.
  - Redirect post-login works.

***

### Task 2.6: Authenticated API Requests and Logout
- **Description:** Attach JWT to API requests and implement logout.
- **Steps:**
  1. Add Authorization header with Bearer token in API fetch.
  2. Implement logout clearing token and redirect to login.
- **AI Sub-prompt:**
  ```
  Modify frontend API calls to include JWT token in headers and add logout to clear token and redirect.
  ```
- **Self-test:**
  - Protected routes function.
  - Logout clears session.

***

## Phase 3: Testing, Debugging, and Deployment

### Task 3.1: Unit and Integration Tests
- **Description:** Write test suites for backend and frontend.
- **Steps:**
  1. Use Jest/Vitest for backend route tests.
  2. Use React Testing Library for frontend components.
- **AI Sub-prompt:**
  ```
  Generate sample Jest tests for backend APIs and React Testing Library unit tests for frontend components.
  ```
- **Self-test:**
  - Tests run and pass successfully.

***

### Task 3.2: End-to-end Debugging and Refinement
- **Description:** Manually test full user flows, fix bugs.
- **Steps:**
  1. Perform full flow: registration, login, browsing, adding cart, ordering.
  2. Inspect/fix bugs.
- **AI Sub-prompt:**
  ```
  Provide debugging tips and troubleshooting steps for backend and frontend errors.
  ```
- **Self-test:**
  - Smooth user flow with no crashes.

***

### Task 3.3: Production Build and Deployment
- **Description:** Prepare apps for production and deploy.
- **Steps:**
  1. Add env var support for backend/frontend.
  2. Build Next.js frontend (e.g., `next build`).
  3. Provide deployment instructions for Vercel (frontend) and Heroku/Cloud for backend.
- **AI Sub-prompt:**
  ```
  Generate production build and deployment instructions for Next.js frontend and Fastify backend with environment variables setup.
  ```
- **Self-test:**
  - Deployed apps function with env vars and connect properly.

***
