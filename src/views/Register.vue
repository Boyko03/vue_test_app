<template>
  <div>
    <div class="d-flex justify-content-center">
      <b-card
        class="my-3"
        header="Sign Up"
        border-variant="secondary"
        header-border-variant="secondary"
      >
        <b-form id="myForm" @submit="onSubmit" v-if="show" :validated="valid" :novalidate="true">
          <b-form-group id="name=input-group" label="Name:" label-for="name">
            <b-form-input
              id="name"
              v-model="form.name"
              required
              placeholder="Your name"
            ></b-form-input>
          </b-form-group>

          <b-form-group
            id="email-input-group"
            label="Email address:"
            label-for="email"
            description="We'll never share your email with anyone else."
          >
            <b-form-input
              id="email"
              v-model="form.email"
              type="email"
              required
              placeholder="Enter email"
            ></b-form-input>
          </b-form-group>

          <b-form-group id="password-input-group" label="Password:" label-for="password">
            <b-form-input
              type="password"
              id="password"
              v-model="form.password"
              aria-describedby="password-help-block"
              placeholder="Enter password"
              required
              minlength="8"
              maxlength="20"
            ></b-form-input>
            <b-form-text id="password-help-block">
              Your password must be 8-20 characters long, contain letters and numbers, and must not
              contain spaces, special characters, or emoji.
            </b-form-text>
          </b-form-group>

          <b-form-group id="checkbox-input-group">
            <b-form-checkbox v-model="form.captcha" value="captcha" id="captcha" required>Captcha</b-form-checkbox>
          </b-form-group>

          <b-form-group>
            <b-button type="submit" variant="primary">Sign Up</b-button>
            <label aria-describedby="have-an-account-help-block" />
            <b-form-text id="have-an-account-help-block">
              <b-link to="/login" class="card-link">Already have an account? Sign In now!</b-link>
            </b-form-text>
          </b-form-group>
        </b-form>
      </b-card>
    </div>
    <!--
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
    -->
  </div>
</template>

<script>
  import {
    BForm,
    BFormGroup,
    BFormInput,
    BFormCheckbox,
    BFormText,
    BButton,
    BCard,
    BLink,
  } from 'bootstrap-vue';
 
  export default {
    name: 'Register',
    components: {
      BForm,
      BFormGroup,
      BFormInput,
      BFormCheckbox,
      BFormText,
      BButton,
      BCard,
      BLink,
    },
    data() {
      return {
        form: {
          name: '',
          email: '',
          password: '',
          captcha: false
        },
        show: true,
        valid: false
      }
    },
    methods: {
      onSubmit(evt) {
        this.valid = true

        var form = document.getElementById('myForm')
        if (form.checkValidity() === false) {
          evt.preventDefault();
          evt.stopPropagation();
        }
        else {
          alert(JSON.stringify(this.form))
        }
      },
    }
  }
</script>