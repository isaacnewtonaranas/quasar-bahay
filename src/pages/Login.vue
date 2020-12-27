<template>
  <div class="q-pa-lg" style="max-width: 400px">
    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="username"
        label="Your username *"
        hint="No space"
        lazy-rules
        :rules="[ val => val && val.length > 3 || 'Please type something']"
      />
      <q-input
        filled
        type="password"
        v-model="password"
        label="Your password *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Please type your password'
        ]"
      />
      <div class="text-caption text-grey-7 text-italic">
        By clicking here, you registering, you accept the rules....
      </div>
      <q-toggle v-model="accept" label="I accept the license and terms" />
      <div>
        <q-btn label="Submit" type="submit" color="negative" /> 
        <q-btn label="Reset" type="reset" color="blue" flat class="q-ml-sm" />
      </div>
    </q-form>
  </div>
</template>
<script>
export default {
  data () {
    return {
      username: null,
      password: null,
      confirmPassword: null,
      accept: false
    }
  },

  methods: {
    onSubmit () {
      if (this.accept !== true) {
        this.$q.notify({
          color: 'red-5',
          textColor: 'white',
          icon: 'warning',
          message: 'You need to accept the license and terms first'
        })
      } else {
        if(this.password==this.confirmPassword){
          this.$q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'fa fa-bath',
            message: 'Submitted'
          })
        }else{
          this.$q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'Your password didn\'t match'
          })
        }
      }
    },

    onReset () {
      this.username = null
      this.password = null
      this.confirmPassword = null
      this.accept = false
    }
  }
}
</script>