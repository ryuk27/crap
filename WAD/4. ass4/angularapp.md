### **Step 1: Set Up Angular Project**

1. **Install Node.js** if you haven’t yet: [Download Node.js](https://nodejs.org/).
2. **Install Angular CLI** globally on your computer by running this in your command prompt or terminal:

   ```bash
   npm install -g @angular/cli
   ```
3. **Create a new Angular project**:

   * Open **VS Code**.
   * Open the **Terminal**.
   * Run the following command to create your project:

     ```bash
     ng new user-auth-app
     ```

     Follow the prompts and choose **CSS** for styling.
4. **Navigate to your project folder**:

   ```bash
   cd user-auth-app
   ```

---

### **Step 2: Create Components for Registration, Login, and Profile**

In the terminal, run these commands to create the components:

1. **Register Component**:

   ```bash
   ng generate component register
   ```

2. **Login Component**:

   ```bash
   ng generate component login
   ```

3. **Profile Component**:

   ```bash
   ng generate component profile
   ```

---

### **Step 3: Set Up Routing to Navigate Between Pages**

1. **Open `app-routing.module.ts`** file inside the `src/app` folder.
2. Replace the code with this:

```typescript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { RegisterComponent } from './register/register.component';
import { LoginComponent } from './login/login.component';
import { ProfileComponent } from './profile/profile.component';

const routes: Routes = [
  { path: 'register', component: RegisterComponent },
  { path: 'login', component: LoginComponent },
  { path: 'profile', component: ProfileComponent },
  { path: '', redirectTo: '/login', pathMatch: 'full' }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

This code allows you to switch between pages like **Register**, **Login**, and **Profile**.

---

### **Step 4: Create the Register Page**

1. **Edit the `register.component.ts`** file to handle registration logic:

```typescript
import { Component } from '@angular/core';
import { Router } from '@angular/router';

@Component({
  selector: 'app-register',
  templateUrl: './register.component.html',
  styleUrls: ['./register.component.css']
})
export class RegisterComponent {
  user = { username: '', password: '' };

  constructor(private router: Router) {}

  onRegister() {
    // Store the user data in local storage
    localStorage.setItem('user', JSON.stringify(this.user));
    alert('Registration successful!');
    this.router.navigate(['/login']);
  }
}
```

2. **Create the Registration Form** in `register.component.html`:

```html
<div>
  <h2>Register</h2>
  <form (ngSubmit)="onRegister()">
    <label>Username:</label>
    <input type="text" [(ngModel)]="user.username" name="username" required />
    
    <label>Password:</label>
    <input type="password" [(ngModel)]="user.password" name="password" required />
    
    <button type="submit">Register</button>
  </form>
</div>
```

---

### **Step 5: Create the Login Page**

1. **Edit `login.component.ts`** to handle login logic:

```typescript
import { Component } from '@angular/core';
import { Router } from '@angular/router';

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent {
  user = { username: '', password: '' };

  constructor(private router: Router) {}

  onLogin() {
    const storedUser = JSON.parse(localStorage.getItem('user') || '{}');
    
    if (storedUser.username === this.user.username && storedUser.password === this.user.password) {
      alert('Login successful!');
      this.router.navigate(['/profile']);
    } else {
      alert('Invalid credentials');
    }
  }
}
```

2. **Create the Login Form** in `login.component.html`:

```html
<div>
  <h2>Login</h2>
  <form (ngSubmit)="onLogin()">
    <label>Username:</label>
    <input type="text" [(ngModel)]="user.username" name="username" required />
    
    <label>Password:</label>
    <input type="password" [(ngModel)]="user.password" name="password" required />
    
    <button type="submit">Login</button>
  </form>
</div>
```

---

### **Step 6: Show Profile Data**

1. **Edit `profile.component.ts`** to display the logged-in user:

```typescript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-profile',
  templateUrl: './profile.component.html',
  styleUrls: ['./profile.component.css']
})
export class ProfileComponent implements OnInit {
  user: any = {};

  ngOnInit() {
    this.user = JSON.parse(localStorage.getItem('user') || '{}');
  }
}
```

2. **Display the User Data** in `profile.component.html`:

```html
<div>
  <h2>Profile</h2>
  <div *ngIf="user.username">
    <p><strong>Username:</strong> {{ user.username }}</p>
    <p><strong>Password:</strong> {{ user.password }}</p>
  </div>
  <div *ngIf="!user.username">
    <p>No user data found. Please <a routerLink="/login">login</a>.</p>
  </div>
</div>
```

---

### **Step 7: Run Your Application**

1. In the **terminal**, run the following command to start the application:

   ```bash
   ng serve
   ```
2. Open your browser and visit **`http://localhost:4200`**.
