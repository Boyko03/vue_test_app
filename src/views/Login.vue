<template>
  <div>
    <div class="d-flex justify-content-center">
      <b-card
        class="my-3"
        header="Sign In"
        border-variant="secondary"
        header-border-variant="secondary"
      >
        <b-form id="myForm" @submit="onSubmit" v-if="show" :validated="valid" :novalidate="true">
          <b-form-group
            id="email-input-group"
            label="Email address:"
            label-for="email"
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
              placeholder="Enter password"
              required
              minlength="8"
              maxlength="20"
            ></b-form-input>
          </b-form-group>

          <b-form-group>
            <b-button type="submit" variant="primary">Sign In</b-button>
            <label aria-describedby="not-have-an-account-help-block" />
            <b-form-text id="not-have-an-account-help-block">
              <b-link to="/register" class="card-link">Don't have an account? Sign Up now!</b-link>
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
      BFormText,
      BButton,
      BCard,
      BLink,
    },
    data() {
      return {
        form: {
          email: '',
          password: '',
        },
        show: true,
        valid: false,
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
