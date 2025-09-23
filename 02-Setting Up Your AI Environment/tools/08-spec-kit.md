### 1. INSTALL SPEC-KIT 
```
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```
### 2. Create project
```
specify init <PROJECT_NAME>
specify check
```
##​​​# 3. Create project ( prd ,  using ai chat )

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

---
Line:

https://docs.claude.com/en/docs/claude-code/setup

https://github.com/QwenLM/qwen-code
