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
