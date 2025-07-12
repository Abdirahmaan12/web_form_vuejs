<template>
  <signupform v-if="!showSuccess" @form-success="showSuccess = true" />
  <success v-else @reset="showSuccess = false" />
</template>

<script>
import signupform from './components/signupform.vue'
import success from './components/success.vue'
export default {
  name: 'App',
  data() {
    return {
      showSuccess: false
    }
  },
  components: { signupform, success }
}
</script>
