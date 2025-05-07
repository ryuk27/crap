## 🧱 **HTML & Structure – Viva Q\&A**

### 1. ❓ What is the purpose of `<!DOCTYPE html>`?

**✅ Answer:** It tells the browser to render the page in HTML5 mode, ensuring modern features and standards are used.

### 2. ❓ Why is `lang="en"` used in the `<html>` tag?

**✅ Answer:** It declares the language of the document (English), which helps with accessibility tools and search engines.

### 3. ❓ What does `<meta name="viewport">` do?

**✅ Answer:** It makes the layout responsive on mobile devices by controlling scaling and dimensions.

### 4. ❓ Why did you split login and dashboard into two sections?

**✅ Answer:** To show or hide them based on authentication state (logged in or not), which improves user experience and simulates a real login flow.

### 5. ❓ What's the difference between `id` and `class`?

**✅ Answer:** `id` is unique and used to target a specific element, while `class` can be shared across multiple elements for styling and grouping.

---

## 🎨 **CSS & Bootstrap – Viva Q\&A**

### 6. ❓ What is Bootstrap, and why are you using it?

**✅ Answer:** Bootstrap is a popular CSS framework that provides pre-designed classes for responsive layouts, buttons, forms, etc., making development faster and consistent.

### 7. ❓ What does `.card-border-left` do?

**✅ Answer:** It's a custom class that applies a left border to Bootstrap cards using `border-left` for visual emphasis.

### 8. ❓ How does `@media (max-width:768px)` help?

**✅ Answer:** It applies styles when the screen is less than or equal to 768px wide (mobile view), making the layout responsive.

### 9. ❓ What does `.d-none`, `.mt-3`, `.shadow`, `.text-primary` mean?

**✅ Answer:**

* `.d-none`: Hides the element
* `.mt-3`: Adds top margin
* `.shadow`: Adds shadow for depth
* `.text-primary`: Applies primary theme color

### 10. ❓ Why use `bg-success`, `border-warning`, etc.?

**✅ Answer:** These Bootstrap utility classes apply background/border colors that convey meaning (success, warning, etc.) and improve visual feedback.

---

## 🛠️ **JavaScript Logic – Viva Q\&A**

### 11. ❓ What does `DOMContentLoaded` do?

**✅ Answer:** It ensures the script runs only after the HTML is fully loaded in the browser.

### 12. ❓ How does the login logic work?

**✅ Answer:** It checks if the entered username and password match the predefined values (`admin` and `1q2w3e4r`). If yes, it shows the dashboard and stores the login state in `sessionStorage`.

### 13. ❓ Why use `sessionStorage` instead of `localStorage`?

**✅ Answer:** `sessionStorage` only lasts for the current tab session, which is more secure for temporary login states.

### 14. ❓ What happens on wrong credentials?

**✅ Answer:** An error message appears for 3 seconds using `setTimeout()` and then hides again.

### 15. ❓ What does `e.preventDefault()` do in the form?

**✅ Answer:** It prevents the form from submitting and reloading the page, allowing us to handle login with JavaScript.

### 16. ❓ What does `sidebar.classList.toggle('show')` do?

**✅ Answer:** It toggles the visibility of the sidebar on mobile by adding/removing the `show` class.

---

## 🔒 **Login Logic & Security – Viva Q\&A**

### 17. ❓ Is using hardcoded credentials secure?

**✅ Answer:** No. Hardcoded login info is only acceptable for demos or small projects. In real apps, credentials should be checked on a backend server securely.

### 18. ❓ What happens if I refresh after logging in?

**✅ Answer:** Since `sessionStorage` still holds the `"loggedIn"` value, the dashboard view remains visible.

### 19. ❓ How can you improve this login system?

**✅ Answer:** By using a backend API for secure login validation and storing session tokens/cookies instead of hardcoded checks.

---

## 🧩 **Functionality and UX – Viva Q\&A**

### 20. ❓ What do the dashboard cards represent?

**✅ Answer:** They show metrics like number of exams, students, upcoming exams, and pass rate using a clean and summarized layout.

### 21. ❓ How is progress shown for top students?

**✅ Answer:** Using Bootstrap’s progress bars (`.progress-bar`) styled with inline `width` values to represent their percentage scores visually.

### 22. ❓ Why is there a sidebar toggle button on small screens?

**✅ Answer:** On mobile, screen space is limited. The toggle allows hiding/showing the sidebar as needed for better user experience.

---

## 🧾 **Short Logic Code for Paper (Simplified Version)**

Here’s a paper-friendly version of your JavaScript logic, shortened and annotated:

```javascript
// On DOM load
document.addEventListener('DOMContentLoaded', () => {
  // Get elements
  let loginForm = document.getElementById('loginForm');
  let error = document.getElementById('login-error');
  let dashboard = document.getElementById('dashboard-content');
  let loginPage = document.getElementById('login-container');

  // Show dashboard if already logged in
  if (sessionStorage.getItem('loggedIn') === 'true') {
    loginPage.style.display = 'none';
    dashboard.style.display = 'block';
  }

  // On login form submit
  loginForm.addEventListener('submit', e => {
    e.preventDefault();
    let u = document.getElementById('username').value;
    let p = document.getElementById('password').value;
    if (u === 'admin' && p === '1q2w3e4r') {
      sessionStorage.setItem('loggedIn', 'true');
      loginPage.style.display = 'none';
      dashboard.style.display = 'block';
    } else {
      error.classList.remove('d-none');
      setTimeout(() => error.classList.add('d-none'), 3000);
    }
  });

  // Logout logic
  document.getElementById('logout-btn')?.addEventListener('click', () => {
    sessionStorage.removeItem('loggedIn');
    dashboard.style.display = 'none';
    loginPage.style.display = 'block';
  });
});
```

---
