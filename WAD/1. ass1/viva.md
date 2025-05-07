## 🎓 **Viva Questions – Categorized by Section**

### 1. 🧱 **HTML & Structure**

* What is the purpose of `<!DOCTYPE html>`?
* Why is `lang="en"` important in the `<html>` tag?
* What does the `<meta name="viewport">` tag do?
* Why did you split login and dashboard into two sections?
* What role do the `<main>`, `<nav>`, and `<div class="row">` elements play?
* What is the difference between `id` and `class` in HTML?

---

### 2. 🎨 **CSS & Bootstrap**

* What is Bootstrap? Why are we using it?
* What does `.card-border-left` do?
* How does `@media (max-width:768px)` help with responsiveness?
* What’s the purpose of using `.d-none`, `.mt-3`, `.shadow`, `.text-primary`, etc.?
* Why do we use classes like `bg-success` or `border-warning`?

---

### 3. 🛠️ **JavaScript Logic**

* What does `document.addEventListener('DOMContentLoaded')` do?
* How does the login logic work?
* Why is `sessionStorage` used instead of `localStorage`?
* What will happen if wrong credentials are entered?
* What happens when the logout button is clicked?
* Why is `e.preventDefault()` used in the login form?
* What does `sidebar.classList.toggle('show')` do?

---

### 4. 🔒 **Login Logic & Security**

* Are hardcoded credentials (`admin`, `1q2w3e4r`) secure?
* How can this login system be improved for real-world use?
* What happens to the session when the page is refreshed?

---

### 5. 🧩 **Functionality and UX**

* What do the dashboard cards represent?
* How is progress shown for top students?
* Why is there a sidebar toggle on small screens?
* What’s the use of the `<progress-bar>`? How does its width relate to the data?

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
