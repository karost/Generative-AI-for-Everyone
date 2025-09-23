### 1. INSTALL SPEC-KIT 
```
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```
### 2. Create project
```
specify init <PROJECT_NAME>
specify check
```
### 3. Create project details

draft : 1
```
Project Name : Marketing Ai
Project Description:
Build a responsive, bilingual (Thai/English) educational website teaching advertising and digital marketing fundamentals. The platform presents self-paced courses, modular lessons, and interactive quizzes. Its design emphasizes accessibility, modularity, and modern standards, with robust support for both Thai and English learners.

Functional Requirements:

The homepage welcomes users and introduces core marketing and advertising principles.

Courses are modular; each major topic (such as Social Media, SEO, Google Ads, Content Marketing) is a section with its own page and navigation.

Each course contains a series of text-based lessons (minimum two per course). At the end of every lesson are at least two quiz questions to reinforce learning with instant feedback.

Navigation bar includes Home, Courses, About, and Contact. Menus adapt to the selected language.

All course, lesson, quiz content, and UI labels are stored in structured JSON for easy updates and scalability.

Sample media (such as icons or images) are integrated for lesson illustration, using placeholders that can be swapped later.

Core UI components (lessons, quizzes, nav, language switcher) are written as self-contained, reusable function components.

Users can switch between Thai and English at any time. Their language preference is automatically detected via browser locale, but any manual change is persisted and remembered on return.

The website’s design is fully mobile-responsive and leverages Tailwind CSS for rapid prototyping and consistent theming.

Full Functional Detail – Use Cases:

Users access the homepage to see an overview of site offerings and explanation of key digital marketing concepts.

A user clicks “Courses” to browse topics. Selecting a course takes them to that course’s landing page with a list of lessons.

Browsing a lesson, the user reads content and at the end completes a multiple-choice quiz. After answering, the user immediately receives feedback and can revisit explanations.

Any time, the user may switch the interface between Thai and English using a toggle. All visible UI, lesson, and quiz content updates live. On next visit, the last-used language reappears.

The About page details the goals of the platform and introduces the team or philosophy behind the tutorials.

The Contact page provides a method (form or email) for users to reach out with questions or feedback, in either language.

Admins or maintainers can add new courses, lessons, and quizzes by updating or adding to the site’s JSON content files; no code changes are required for new content.

Non-Functional Requirements:

Consistent, modern visual identity and UX, with intuitive navigation and fast loading times.

Accessibility: All navigation, forms, and interactive elements must be usable via keyboard and screen readers.

Performance: All assets optimized for quick delivery, and minimal client-side scripting for best-in-class speed on mobile and desktop.

Security: Contact forms must validate and sanitize user input to prevent spam or injection attacks.

Scalability: JSON-driven architecture enables future expansion (such as more courses, additional languages, or media types) without major codebase changes.

Internationalization: All user-facing content (labels, navigation, lessons, quizzes) must be localizable. Language switch and persistence must be seamless, using cookies or localStorage.

Cross-browser compatibility, supporting evergreen desktop and mobile browsers.

This expanded scope and detailed coverage ensure the final app meets professional standards for international, educational platforms and can be smoothly maintained or grown in the future.
```
draft: 2
```
***
### Project name : Marketing Ai
### Project Description

This project is a full-stack web application built with Next.js and Tailwind CSS that provides educational resources about advertising and digital marketing. The website is designed to serve both Thai and English-speaking users. Users can switch languages, and the preference is remembered for subsequent visits. Features include modular course content (with presentations, lessons, and quizzes), a dynamic navigation bar, and responsive design optimized for all devices. The site aims to help users learn marketing strategies and tools, with localized context for Thailand's fast-evolving digital landscape.[1][2]

***

### Use Case Scenarios (All User Activity)

1. User visits the homepage and reads a bilingual introduction to digital marketing fundamentals.
2. User navigates to the “Courses” section and selects a course (either in Thai or English).
3. User goes through multi-lesson modules (e.g., Social Media, SEO, Google Ads, Content Marketing), reading lesson content and viewing embedded presentations.
4. At the end of each lesson, user answers interactive quiz questions and receives instant feedback.
5. User switches between Thai and English; their language preference is remembered using cookies or local storage.
6. User explores sample marketing product presentations, which are regionally relevant.
7. User searches or browses lesson topics, selects 1 out of 10 highlighted marketing content products to view a detailed presentation.
8. Admin uploads new JSON lesson data or revises courses without code changes.
9. Repeated visits: User’s preferred language and completed quizzes/lessons are loaded, showing progress.
10. User accesses site on desktop, mobile, or tablet; layout adapts perfectly.

***

### Functional Requirements

- The site must provide a homepage with bilingual introductory content about digital marketing and advertising fundamentals.
- Users must be able to navigate among Home, Courses, About, and Contact sections via a dynamic navigation bar.
- Each course must be presented in modular pages/components; every module contains at least 2–3 lessons and interactive quizzes.
- All course, lesson, and quiz data are stored in JSON format for easy updating and extensibility.
- The site must display marketing product presentations (10 total) sourced from Thai marketing trends; each is offered in Thai with full details.
- Users can switch language at any time between Thai and English; the site remembers the choice across sessions.
- The application uses Next.js and Tailwind CSS, providing full stack support for SSR, authentication, storage, and responsive UI.
- The system loads user language preference, completed lessons, and scores automatically for returning visitors.
- Placeholders for images and icons are used for visual illustration, and real images can be added by admins.

***

### Non-Functional Requirements

- Application must load in less than 2 seconds for standard broadband connections in Thailand.
- Must support all major browsers and mobile devices with responsive, accessible UI.
- Site language switching must be instant and persist for authenticated and unauthenticated users.
- Data stored in JSON must not require server restarts for updates; hot reload for content editors.
- Security: No user data is shared; any quiz results are stored locally or securely handled by backend APIs.
- High availability setup for public access, with uptime >99.9%.
- SEO and marketing standards: Pages use proper meta tags, structured data, and localized SEO for both languages.
- Support for future third language (extensible i18n architecture).
- Accessible: Follows W3C accessibility guidelines and color contrast for all UI elements.
- Logs and analytics compliant with privacy standards in Thailand.

***

### Ten Thai Marketing Content Presentation Topics (with Full Details)

1. **AI-Powered Personalization in Thai Marketing**  
 Details: แสดงวิธีที่แบรนด์ต่าง ๆ ใช้ AI เพื่อปรับแต่งโฆษณาและเสนอสินค้าให้เหมาะกับลูกค้าแต่ละคน เช่น แนะนำสินค้าในแอปช็อปปิ้งคนไทยโดยอ้างอิง Big Data.[3][1]

2. **Influencer Marketing Trends in Thailand**  
 Details: วิเคราะห์ความสำคัญของไมโครอินฟลูเอนเซอร์ในการเข้าถึงกลุ่มเป้าหมาย โดยยกตัวอย่างแคมเปญที่ใช้ผู้ติดตามหลักหมื่น สร้างยอดขายสูงขึ้นผ่าน Instagram/TikTok.[1][3]

3. **Social Commerce Ecosystem**  
 Details: อธิบายการเปลี่ยนแปลงการซื้อขายในโซเชียลมีเดีย เช่น Facebook Live, Shopee Live พร้อมเทคนิคสร้างอีเวนต์ไลฟ์ช็อปปิ้งที่มีส่วนลด.[4][3]

4. **Short-Form Video Dominance**  
 Details: วิเคราะห์ว่าคลิปสั้นบน TikTok/Reels ได้ผลกับกลุ่มคนไทยอย่างไรและแนวทางการสร้างคอนเทนต์วิดีโอที่มีอัตราการเข้าชมสูง.[1]

5. **SEO Strategies for Thai Businesses**  
 Details: สอนวิธีการปรับแต่งเว็บไซต์ให้ติดอันดับ Google ประเทศไทย ใช้คีย์เวิร์ดท้องถิ่น และการสร้างคอนเทนต์ตอบคำถามที่เจาะกลุ่มเป้าหมายโดยตรง.[4]

6. **Voice Search Optimization and Smart Devices**  
 Details: แนะนำการปรับเว็บไซต์ให้รองรับคำค้นด้วยเสียง รองรับเทรนด์สมาร์ทโฟนและสมาร์ทโฮมที่เติบโตในไทย.[3][1]

7. **First-Party Data Collection after Privacy Regulations**  
 Details: อธิบายเทคนิคการเก็บข้อมูล (เช่น สมัครสมาชิก รับส่วนลด) ให้ถูกต้องตามกฎหมาย PDPA ประเทศไทย พร้อมเทคนิคใช้ข้อมูลสื่อสารส่วนบุคคลอย่างปลอดภัย.[1]

8. **Sustainability Marketing and Circular Economy**  
 Details: วิเคราะห์ตัวอย่างธุรกิจไทยที่ใช้กลยุทธ์การผลิตแบบปกป้องสิ่งแวดล้อม เช่น ร้านค้าที่เติมเต็มสินค้าโดยใช้บรรจุภัณฑ์รีไซเคิล.[3]

9. **Omnichannel Engagement for Thai Consumers**  
 Details: แนวทางเชื่อมต่อประสบการณ์ลูกค้าระหว่างหน้าร้าน ออนไลน์ แอปมือถือ และโซเชียลมีเดีย แบบไร้รอยต่อ.[4][1]

10. **Localized Content for Thai Audiences**  
 Details: กำหนดหลักการสร้างคอนเทนต์ที่ใช้ภาษาไทย รูปภาพสถานที่ท่องเที่ยว หรือประเพณี เพื่อสร้างความเชื่อมโยงกับผู้ชมในประเทศ.[5]

***

This improved documentation ensures completeness and reliability for developers, stakeholders, and Thai marketing educators, covering all relevant functional, non-functional requirements, and scenario details necessary for implementation of a bilingual full-stack application using Next.js and Tailwind CSS.[6][2][5][4][3][1]

[1](https://www.inspiradigitalagency.com/digital-marketing-trends-in-thailand/)
[2](https://nextjs.org/docs/app/guides/internationalization)
[3](https://www.marketingthai.or.th/en/10-marketing-trends-2025-of-mat/)
[4](https://www.inspiradigitalagency.com/marketing-channels-in-thailand/)
[5](https://www.marketingoops.com/reports/thai-and-asian-content-trend/)
[6](https://dev.to/codegino/building-a-multilingual-nextjs-app-using-the-new-app-directory-2anf)
[7](https://www.geeksforgeeks.org/blogs/best-full-stack-project-ideas/)
[8](https://www.theseus.fi/bitstream/handle/10024/752615/SueroMartinez_HectorGabriel_thesis.pdf?sequence=2)
[9](https://devchallenges.io/projects/full-stack)
[10](https://www.intuz.com/guide-to-full-stack-development)
[11](https://www.turing.com/blog/full-stack-project-ideas-for-software-developers)
[12](https://www.websiteplanningguide.com/comprehensive-website-functional-requirements/)
[13](https://nextjsstarter.com/blog/nextjs-13-multilingual-sites-app-directory-guide/)
[14](https://www.foreplay.co/post/examples-of-facebook-ads-for-education)
[15](https://metana.io/blog/12-top-full-stack-project-ideas-in-2024/)
[16](https://www.nuclino.com/articles/functional-requirements)
[17](https://blog.adbeat.com/how-4-types-of-education-sites-use-advertising-to-maximize-their-lead-generation/)
[18](https://www.jobalope.com/skills-library/engineering-and-technology/fullstack-developer/digital-marketing-in-a-fullstack-developer-job/)
[19](https://decode.agency/article/functional-requirements-examples/)
[20](https://firdoshkhan.in/top-10-marketing-for-education-case-studies/)
```
### 4. Make constution md 
```
Below is a constitution.md draft tailored for your bilingual advertising and marketing tutorial website project (Next.js/Tailwind, Thai/English) using Spec Kit. This constitution covers code quality, testing standards, user experience consistency, performance guidelines, governance, and project-specific principles aligned with your requirements.[1]

***
/constitution.md updte with:

## Project Governing Principles

### 1. Code Quality  
- All code must be modular, reusable, and readable, following Next.js and Tailwind CSS conventions.  
- All functionality—including multilingual support, quizzes, and data access—should be strictly separated into maintainable components and services.  
- Use only up-to-date, supported dependencies. Avoid unnecessary complexity.

### 2. Testing Standards  
- Unit, integration, and UI tests must be written for every new feature or bug fix.  
- All quizzes, language switching, and lesson navigation must have automated tests covering both Thai and English scenarios.  
- Test coverage targets 90% for critical business logic (course content loading, user progress, and language persistence).

### 3. User Experience Consistency  
- Interfaces should be fully responsive, meeting mobile and desktop usability requirements.  
- Switching between Thai and English must happen instantly, reflecting throughout navigation and content.  
- The site must remember user language and progress reliably on all devices.  
- All images, icons, and content must be relevant to Thai and international contexts.

### 4. Performance Guidelines  
- Initial page load must complete in under 2 seconds for regional users.  
- All JSON data updates and content rendering should be hot-reloaded and not require downtime.  
- UI components must be optimized for accessibility and minimal re-renders.

### 5. Accessibility and Inclusivity  
- Follow W3C and WCAG guidelines for interface color, text contrast, and ARIA attributes.  
- All educational materials must be fully accessible whether viewed in Thai or English.

### 6. Governance and Decision-Making  
- All technical and design decisions must align with these principles and be reviewed via Spec Kit processes before implementation.  
- Team must document reasons for each major technical choice—especially regarding multilingual support, presentation architecture, and data privacy.
- Modifications to the constitution require consensus among lead contributors, documented in /memory/constitution_update_checklist.md.

### 7. Security and Data Privacy  
- No personal user data or quiz results may be exposed to third parties or publicly accessible endpoints.  
- All storage of user preferences (language, quizzes) uses secure, privacy-compliant methods (local storage, cookies with consent).  
- PDPA compliance (for Thailand) infuses all data collection and presentation logic.

### 8. Continuous Improvement  
- Regular audits must occur for accessibility, usability, and language support quality.  
- Community feedback (Thai and English users) is encouraged, and suggestions for improvement integrated via Spec Kit iterative enhancement process.

***

This constitution ensures the project covers critical requirements for code quality, language features, educational integrity, governance, and extensibility—ready for Spec Kit-driven development cycles.[1]

[1](https://github.com/github/spec-kit)
```
### 4. Make constution md
/specify.md with: 

---
Line:

https://docs.claude.com/en/docs/claude-code/setup

https://github.com/QwenLM/qwen-code
