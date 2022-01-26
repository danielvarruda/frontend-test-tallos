<template>
  <div class="page">
    <div class="container-fluid p-4">
      <h2>Funcionários</h2>

      <hr>

      <div class="row p-3">
        <table class="table table-striped table-hover">
          <thead>
            <tr>
              <th>Nome</th>
              <th class="text-center">Setor</th>
              <th class="text-center">E-mail</th>
              <th class="text-center">Ações</th>
            </tr>
          </thead>

          <tbody>
            <tr
              :key="user._id"
              v-for="user in users"
            >
              <td>{{ user.name }}</td>
              <td class="text-center">{{ user.sector && firstUpperCase(user.sector) }}</td>
              <td class="text-center">{{ user.username }}</td>
              <td class="text-center">
                <button class="btn btn-sm btn-info p-1">
                  <router-link
                    class="detalhes"
                    :to="{ name: 'show-user', params: { id: user._id } }"
                  >
                    Detalhes
                  </router-link>
                </button>

                <button class="btn btn-sm btn-warning p-1" style="margin-left: 5px">
                  <router-link
                    class="detalhes"
                    :to="{ name: 'edit-user', params: { id: user._id } }"
                  >
                    Editar
                  </router-link>
                </button>

                <button class="btn btn-sm btn-danger p-1" style="margin-left: 5px" @click.prevent="deleteUser(user._id)">
                  Remover
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from 'vuex'

export default {
  name: 'Users',

  mounted () {
    this.ActionFindUsers()
  },

  computed: {
    ...mapState('users', ['users'])
  },

  methods: {
    ...mapActions('users', ['ActionFindUsers']),
    ...mapActions('users', ['ActionDeleteUser']),

    deleteUser: async function (id) {
      try {
        if (id) {
          await this.ActionDeleteUser(id)
          window.alert('Deletado com sucesso')
        }

        return this.ActionFindUsers()
      } catch (err) {
        console.log(err)
        alert(err.data ? err.data.message : 'Não foi possível deletar o funcionário')
      }
    },

    firstUpperCase: function (work) {
      return work[0].toUpperCase() + work.substr(1).toLowerCase()
    }
  }
}
</script>

<style lang="scss" scoped>
  .detalhes {
    text-decoration: none;
    color: white;
  }
</style>
