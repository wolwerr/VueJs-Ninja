<template>
    <div class="container">
        <h1>Vue.js + Github</h1>
        <p class="lead">
            Página que lista issues de um repositório do Github, usando Vue.js.
        </p>

        <div v-if="response.status === 'error'" class="alert alert-danger">
            {{ response.message }}
        </div>

        <div class="row">
            <div class="col">
                <div class="form-group">
                    <input v-model="username"
                           type="text" class="form-control" placeholder="github username">
                </div>
            </div>

            <div class="col">
                <div class="form-group">
                    <input v-model="repository"
                           type="text" class="form-control" placeholder="github repositório">
                </div>
            </div>

            <div class="col-3">
                <div class="form-group">
                    <button @click.prevent.stop="getIssues()"
                            class="btn btn-success">GO</button>
                    <button @click.prevent.stop="reset()"
                            class="btn btn-danger">LIMPAR</button>
                </div>
            </div>
        </div>

        <br><hr><br>

        <table class="table table-sm table-bordered">
            <thead>
            <tr>
                <th width="100">Número</th>
                <th>Título</th>
            </tr>
            </thead>

            <tbody>
            <tr v-if="loader.getIssues">
                <td class="text-center" colspan="2"><img src="/static/loading.svg" alt=""></td>
            </tr>

            <tr v-if="showIssues"
                v-for="issue in issues"
                :key="issue.number">
                <td>
                    <router-link :to="{ name: 'GitHubIssue',
                                        params: {
                                            name: username,
                                            repo: repository,
                                            issue: issue.number
                                        }}">
                        {{ issue.number }}
                    </router-link>
                </td>

                <td>{{ issue.title }}</td>
            </tr>

            <tr v-if="noIssues">
                <td class="text-center" colspan="2">Nenhuma issue encontrada!</td>
            </tr>
            </tbody>
        </table>
    </div>
</template>


<script>
export default {
  name: 'GitHubeIssues',

  data() {

    return {

    };

  },

  methods: {},
};
</script>
