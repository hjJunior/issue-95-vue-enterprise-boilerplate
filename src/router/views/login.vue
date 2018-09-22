<script>
import Layout from '@layouts/main'
import { authMethods } from '@state/helpers'
import appConfig from '@src/app.config'

export default {
  page: {
    title: 'Log in',
    meta: [{ name: 'description', content: `Log in to ${appConfig.title}` }],
  },
  components: { Layout },
  data() {
    return {
      username: '',
      password: '',
      authError: null,
      tryingToLogIn: false
    }
  },
  methods: {
    ...authMethods,
    // Try to log the user in with the username
    // and password they provided.
    tryToLogIn() {
      this.tryingToLogIn = true
      // Reset the authError if it existed.
      this.authError = null
      return this.logIn({
        username: this.username,
        password: this.password,
      })
        .then(token => {
          this.tryingToLogIn = false

          // Redirect to the originally requested page, or to the home page
          this.$router.push(this.$route.query.redirectFrom || { name: 'home' })
        })
        .catch(error => {
          this.tryingToLogIn = false
          this.authError = error
        })
    },
  },
}
</script>

<template>
  <Layout disabled-nav-bar>
    <BaseCard size="small">
      <form
        :class="$style.form"
        @submit.prevent="tryToLogIn"
      >
        <h5 :class="$style.title">
          App name
        </h5>
        <BaseInput 
          v-model="username" 
          placeholder="Email"
          type="email"
        />
        <BaseInput 
          v-model="password" 
          placeholder="Senha" 
          type="password"
        />
        <BaseCheckbox label="Text here" />
        <BaseButton
          :disabled="tryingToLogIn"
          type="submit"
        >
          <BaseIcon
            v-if="tryingToLogIn"
            name="sync"
            spin
          />
          <span v-else>
            Entrar
          </span>
        </BaseButton>
        <p v-if="authError">
          There was an error logging in to your account.
        </p>
      </form>
    </BaseCard>
  </Layout>
</template>

<style lang="scss" module>
@import '@design';

.title {
  color: #adadad;
  text-align: center;
  text-transform: uppercase;
}

.form {
  text-align: center;
}

</style>
