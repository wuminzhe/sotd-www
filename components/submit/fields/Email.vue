<template>
  <div class="item" :class="errors && errors.length > 0 ? '--has-errors' : ''">
    <input class="text-input" :class="email.length > 0 ? '--is-filled' : ''" type="text" maxlength="50" v-model="email" @input="validate">
    <label class="label">Email <span class="required">(required)</span></label>
    <span class="remaining-characters">{{ 50 - email.length }}</span>
    <ul v-if="errors && errors.length > 0" class="error-list">
      <li v-for="error in errors" class="error-item">{{ error }}</li>
    </ul>
    <p class="help">Email of the primary contact (this will not be made public)</p>
  </div>
</template>

<script>
  import { dispatchErrors } from '~/plugins/mixins'

  var validationTimer

  export default {
    computed: {
      email: {
        get () {
          return this.$store.getters['submit/email']
        },
        set (value) {
          const field = {
            name: 'email',
            value: value
          }
          this.$store.dispatch('submit/updateField', field)
        }
      },
      errors () {
        return this.$store.getters['submit/emailErrors']
      }
    },
    methods: {
      validate () {
        clearTimeout(validationTimer)
        const errors = {
          field: 'email',
          data: []
        }
        validationTimer = setTimeout(() => {
          this.email.indexOf('@') === -1 ? errors.data.push(`Please enter a valid email address`) : ''
          this.dispatchErrors(errors)
        }, 750)
      }
    },
    mixins: [dispatchErrors]
  }
</script>
