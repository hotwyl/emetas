<template>
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-8">
          <div class="card">
            <div class="card-header">{{ 'Login' }}</div>
  
            <div class="card-body">
              <form @submit.prevent="login">
                <div class="mb-3">
                  <label for="email" class="col-form-label">{{ 'Email Address' }}</label>
                  <input
                    v-model="email"
                    type="email"
                    class="form-control"
                    :class="{ 'is-invalid': errors.email }"
                    required
                    autofocus
                  />
                  <div class="invalid-feedback" v-if="errors.email">
                    {{ errors.email }}
                  </div>
                </div>
  
                <div class="mb-3">
                  <label for="password" class="col-form-label">{{ 'Password' }}</label>
                  <input
                    v-model="password"
                    type="password"
                    class="form-control"
                    :class="{ 'is-invalid': errors.password }"
                    required
                  />
                  <div class="invalid-feedback" v-if="errors.password">
                    {{ errors.password }}
                  </div>
                </div>
  
                <div class="mb-3 form-check">
                  <input
                    v-model="remember"
                    type="checkbox"
                    class="form-check-input"
                    id="remember"
                  />
                  <label class="form-check-label" for="remember">
                    {{ 'Remember Me' }}
                  </label>
                </div>
  
                <div class="mb-0">
                  <button type="submit" class="btn btn-primary">
                    {{ 'Login' }}
                  </button>
  
                  <a class="btn btn-link" href="{{ route('password.request') }}">
                    {{ 'Forgot Your Password?' }}
                  </a>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        remember: false,
        errors: {},
      };
    },
    methods: {
      login() {
        // Implement your login logic here
      },
    },
  };
  </script>
  