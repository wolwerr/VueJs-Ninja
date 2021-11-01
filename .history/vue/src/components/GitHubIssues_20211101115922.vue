<template>
    <div class="container">
        <div v-if="loader.getIssue"><img src="/static/loading.svg" alt=""></div>

        <div v-if="!loader.getIssue && issue.number">
            <h1>Issue #{{ issue.number }}</h1>
            <h2>{{ issue.title }}</h2>
            <div>{{ issue.body }}</div>
            <a href="javascript:history.go(-1)" class="btn btn-primary">Voltar</a>
        </div>
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
