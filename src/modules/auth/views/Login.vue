<template>
  <div class="login">
    <div class="card">
      <div class="card-header">
        <i class="fas fa-sign-in-alt"></i> Login
      </div>

      <div class="card-body">
        <form @submit.prevent="submit">
          <div class="form-group mb-1">
            <label for="username">E-mail</label>
            <input type="email" id="username" v-model="form.username" class="form-control" required>
          </div>

          <div class="form-group mb-1">
            <label for="password">Senha</label>
            <input type="password" id="password" v-model="form.password" class="form-control" required>
          </div>

          <div class="form-group mt-3 mb-1">
            <input type="submit" value="Login" class="btn btn-primary col-12">
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  data: () => ({
    form: {
      username: '',
      password: ''
    }
  }),

  methods: {
    ...mapActions('auth', ['ActionLogin']),

    submit: async function () {
      try {
        await this.ActionLogin(this.form)
        this.$router.push({ name: 'home' })
      } catch (err) {
        alert(err.body ? err.body : 'E-mail ou senha incorreta')
      }
    }
  }
}
</script>

<style scoped lang="scss">
  .login {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .card-body {
    min-width: 300px;
  }

  .form-group {
    padding: 10px;
  }
</style>
