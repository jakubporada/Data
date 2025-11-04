Perfect! Now that the login component folder exists, you can set it up properly and integrate it into your Angular app. Here’s the step-by-step:

1️⃣ Add the login page HTML

Open:

src/app/login/login.component.html


Replace its contents with your Tailwind login page:

<div class="min-h-screen flex items-center justify-center bg-gray-100">
  <div class="bg-white shadow-lg rounded-lg w-full max-w-md p-8">
    <div class="text-center mb-6">
      <img src="assets/mantech-logo.png" alt="Mantech Logo" class="mx-auto h-12 mb-4">
      <h2 class="text-2xl font-bold text-gray-800">Employee Login</h2>
    </div>
    
    <form [formGroup]="loginForm" (ngSubmit)="onSubmit()">
      <div class="mb-4">
        <label for="username" class="block text-gray-700 font-semibold mb-2">Username</label>
        <input type="text" id="username" formControlName="username"
               class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
               placeholder="Enter your username">
        <div *ngIf="submitted && f.username.errors" class="text-red-500 text-sm mt-1">
          Username is required.
        </div>
      </div>

      <div class="mb-6">
        <label for="password" class="block text-gray-700 font-semibold mb-2">Password</label>
        <input type="password" id="password" formControlName="password"
               class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
               placeholder="Enter your password">
        <div *ngIf="submitted && f.password.errors" class="text-red-500 text-sm mt-1">
          Password must be at least 6 characters.
        </div>
      </div>

      <button type="submit"
              class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg transition-colors">
        Login
      </button>
    </form>

    <p class="mt-4 text-center text-gray-500 text-sm">
      Forgot your password? <a href="#" class="text-blue-600 hover:underline">Reset it</a>
    </p>
  </div>
</div>

2️⃣ Add TypeScript logic for the login form

Open:

src/app/login/login.component.ts


Add reactive form support:

import { Component } from '@angular/core';
import { FormBuilder, FormGroup, Validators } from '@angular/forms';

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent {
  loginForm: FormGroup;
  submitted = false;

  constructor(private fb: FormBuilder) {
    this.loginForm = this.fb.group({
      username: ['', Validators.required],
      password: ['', [Validators.required, Validators.minLength(6)]]
    });
  }

  get f() {
    return this.loginForm.controls;
  }

  onSubmit() {
    this.submitted = true;

    if (this.loginForm.invalid) return;

    // For now, just log the form values
    console.log('Login successful', this.loginForm.value);
    alert(`Welcome, ${this.loginForm.value.username}!`);
  }
}


Make sure ReactiveFormsModule is imported in app.module.ts:

import { ReactiveFormsModule } from '@angular/forms';

@NgModule({
  imports: [
    BrowserModule,
    ReactiveFormsModule,
    ...
  ],
})
export class AppModule {}

3️⃣ Set up routing to the login page

If you haven’t already, open app.module.ts and add routing:

import { RouterModule, Routes } from '@angular/router';
import { AppComponent } from './app.component';
import { LoginComponent } from './login/login.component';

const routes: Routes = [
  { path: '', component: AppComponent },      // your main page
  { path: 'login', component: LoginComponent } // login page
];

@NgModule({
  imports: [
    BrowserModule,
    ReactiveFormsModule,
    RouterModule.forRoot(routes)
  ],
  declarations: [
    AppComponent,
    LoginComponent
  ],
  bootstrap: [AppComponent]
})
export class AppModule {}

4️⃣ Add a router outlet in your main page

Replace the contents of app.component.html with:

<router-outlet></router-outlet>


Angular will now render pages depending on the route. /login will show your login page.

5️⃣ Run the app
ng serve


Then open:

http://localhost:4200/login


You should see your centered Tailwind Mantech login page, ready to go.

If you want, I can also add a polished background, card animation, and focus effects, so it looks super professional for Mantech.
