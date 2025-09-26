Link : 

https://github.com/github/spec-kit

### 1. SETTUP 

1. Prerequesition 
- nodejs , uv , vs code 
- create account  qwen https://chat.qwen.ai  -> username , password 

2. Install tools 
- qwen code https://github.com/QwenLM/qwen-code  ( first time login must use Qwen OAuth ( qwen accout))

- spec-kit  https://github.com/github/spec-kit 

### 2. CREATE PROJECT

1. Prerequestion information
- PRD (product requirement) -> /specify
- Tech stack ( NextJS-15, Tailwind 4, chadcn/ui) , custom templte -> /plan
- Project Instructions -> /constitution

### 3. FILLING DATA
1. CONSTITUTION: -> /constitution
```




```
3. SPECIFICATION : -> /specify
4. REVIEW PROJECT SPEC
5. IMPLEMENT PROJECT




### 4. Reference info.
```
1. PRD :
## Product Requirement Document: MaMa Food-Delivery 
## 1. ลูกค้า (Customer App)

### 1.1 User Registration & Profile (Latest Policy)
- **Mandatory Registration**: ทุกผู้ใช้ต้องสมัครสมาชิกก่อนใช้งาน/สั่งซื้อ (No Guest Access)
- สมัครด้วย email, เบอร์โทร, หรือ social login (Google/Facebook/Apple)
- **ยืนยันตัวตน**: OTP หรือ email (registration/authentication)
- กรอกข้อมูลโปรไฟล์ (ชื่อ, ที่อยู่, เบอร์, payment)
- แก้ไขโปรไฟล์, เปลี่ยนรหัส, ลืมรหัส, ลบบัญชี (PDPA/GDPR compliance)
- Session timeout, SSL/TLS, ไม่ให้ email/phone ซ้ำ

### 1.2 Core Flow & Screens (Frictionless, Conversion-Focused)
- **Home/Menu**: Search bar, filter by category, featured/popular, food thumbnails, large image on click
- **Cart**: Sticky cart icon, cart drawer/sheet, edit/remove/add quantity, promo/coupon display/apply, auto-save cart
- **Order Review/Checkout**: Short steps (2-3 max), address autofill/map picker, coupon input, progress/step bar
- **Payment**: e-wallet/online/QR/cash, large sticky "Pay Now", summary
- **Live Support**: In-app chat/support available during checkout
- **Push Notifications**: Order status, abandoned cart, promo/coupon, delivery reminder
- **Order Tracking**: Real-time from kitchen to delivery to feedback/review flow

### 1.3 UX/Feature Set
- Social/email registration + mandatory profile
- Auto-save and restore cart across sessions
- Sticky CTAs, mobile-first responsive UI
- Loyalty program, gamification, coupons
- Review & rate menu/restaurant with image upload
- เก็บ/แสดง order history & status
- Sync, notification, tracking—all real-time

### 1.4 for customer page must support switch in three language : Thai, English, China. Ai must make a full reseach for next.js 15, tailwind 4, chadcn/ui that support multilanguage  

---

## 2. ร้านขายอาหาร (Vendor/Restaurant Panel)

### 2.1 Vendor Registration & Profile
- **Mandatory registration & verification**: Fill in shop name, type, phone, email, bank account, upload verification docs (business verification), set operation hours, profile pics/logos, admin approval required before product listing/opening for orders
- Profile edit, reset password, close account possible only for verified vendors
- No guest/vendor bypass, all vendors must be approved (compliance)

### 2.2 Menu/Product Management
- Add/edit/delete menu and product listings
- Upload or take photos from mobile (system auto-resizes for thumbnail & large)
- Enter: name, price, description, stock, category, promo per menu
- Menu status: open/close, batch update, export menu list
- Live preview before publish, can change image/data any time
- Product moderation for new items/images by admin (if enabled)

### 2.3 Order Queue & Management
- Real-time new order queue: Accept/reject, change status (cooking, ready, delivered)
- View details: order list, customer address, delivery instructions, notes
- Order slip print, status update/notification to customer

### 2.4 Analytics, Promo, and Review
- Sales dashboard (day/month), analytic graphs for bestsellers, filter by menu/period, export sales data
- Create menu/store promotions, coupon for store, use platform-wide ones from admin
- Review center: view/respond to reviews/feedback, alert for complaints/negative reviews

### 2.5 Notifications & Alerts
- New order, review, out-of-stock, auto-notify (real-time)
- Set open/close shop, set delivery zones

---

## 3. Admin Panel (Backend)

### 3.1 User, Vendor, Content & Role Management
- User/vendor approve/suspend/edit, manage roles (Super Admin, Order Manager, Vendor Manager, Delivery Manager, Promotion Analyst, Accountant, Support)
- **Vendor onboarding**: Approve vendor documents before activation
- Product/Menu moderation: Approve menu/image before live (optional), see image history/compare versions
- Track all account actions (log/security)
- Search, filter, export data for any user/vendor/accounting/reports
- Set/assign/ban/reset/approve/reject users, vendors

### 3.2 Dashboard & Reporting
- Overview dashboard: Sales, orders, real-time alerts, analytic graphs, segmented by day/month/store
- Order Management: Monitor, assign (auto/manual) drivers, change/cancel/refund orders, live map tracking of deliveries
- Vendor Management: Approve/reject/suspend/create, edit profile/menus, inspect store commissions, analytics
- Delivery Zone Management: Draw polygons/circles on map, set price per zone, see driver status
- Promotion/Coupon Center: Create/assign/manage/analytic for both platform-wide and per-shop coupons
- Review & Complaint Center: View/resolve/escalate all reports, generate complaint analytics, manage problematic content/cases
- Accounting/Reporting: Settlement reconciliation for shop/driver payouts, export all reports/statements

### 3.3 Data Security & Compliance
- All data over SSL/TLS
- Personal fields encrypted, PDPA/GDPR compliance, deletion self-service for users/vendors
- Session timeout, log all critical actions

---

## 4. Flow, API, and Data Format

### 4.1 Core Flows
#### Customer:
- Register/Login → Auth via OTP/email/social → Profile setup → Browse → Cart → Checkout (+payment) → Order Track → Review
- Cannot use platform unless registered/verified

#### Vendor:
- Register → Upload verification doc → Admin approval → Set Profile/Store, add menu/product/image → Start receiving orders

#### Admin:
- Approve user/vendor, manage product content, manage orders/deliveries, review system logs/analytics

### 4.2 Key API Endpoints (must-have, unified set)
#### User/Account:
- `/api/user/register`, `/api/auth/login`, `/api/auth/otp-verify`, `/api/profile/edit`, `/api/password-reset`, `/api/logout`, `/api/user/avatar-upload`
- Must validate no duplicate email/phone

#### Vendor/Store:
- `/api/vendor/register`, `/api/vendor/document-upload`, `/api/shop/menu-add`, `/api/shop/menu-edit`, `/api/vendor/product/image/upload`, `/api/shop/list`, `/api/vendor/profile-edit`

#### Product/Menu:
- `/api/vendor/product/add`, `/api/product/list`, `/api/product/detail`, `/api/vendor/product/image/upload` (with auto-resize/compress)

#### Order:
- `/api/order/create`, `/api/order/update`, `/api/order/assign`, `/api/order/tracking`

#### Promotions/Coupons:
- `/api/coupon/apply`, `/api/promotion/add`, `/api/promotion/distribute`, `/api/promotion/analytics`

#### Admin & Review:
- `/api/admin/approve/reject`, `/api/user/role`, `/api/review/list`, `/api/support/ticket`

#### Delivery:
- `/api/zone/list`, `/api/zone/set`, `/api/driver/location`, `/api/report/export`

#### Security & Compliance:
- All endpoints must enforce encrypted data, secure validation, and audit logging

### 4.3 Data/Image Handling
- Photo upload: always save as both thumbnail (≥150x150px) and large (≥800x800px), auto-compression, CDN, preview & moderation, optimize for speed/cache
- Image/jpg/png/webp; check security, provide preview before publish
```
---

## 5. None functional Requirement
```
1. Architecture tech stack using full-stack application  
2. Frame work: next.js 15, tailwind 4, chadcn/ui
3. Database: PostgreSQL
4. Template for research and reference in implementation : https://github.com/karost/Generative-AI-for-Everyone/blob/main/04-Using%20Ai%20for%20Deployment/Tool-Kits/spec-kit/lab-food-delivery/nextjs-tailwind-shadcn-template.md
5. UX/UI must responsive to mobile, tablit and desktop but default for customer is mobile
6. for customer page must support switch in three language : Thai, English, China. Ai must make a full reseach for next.js 15, tailwind 4, chadcn/ui that support multilanguage
7. sample ui for customer
- https://github.com/karost/Generative-AI-for-Everyone/blob/main/images/p-food-delivery/ui-01-product-list.png
- https://github.com/karost/Generative-AI-for-Everyone/blob/main/images/p-food-delivery/ui-02-product-details.png
```
3. screen short web template

<img src="https://github.com/karost/Generative-AI-for-Everyone/blob/main/images/p-food-delivery/ui-01-product-list.png" width="400">
<img src="https://github.com/karost/Generative-AI-for-Everyone/blob/main/images/p-food-delivery/ui-02-product-details.png" width="400">

