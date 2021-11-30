<template>
  <div class="home">
    <h1>Home</h1>

    <form @submit.prevent="savar">
      <input type="text" v-model="insert.nome" />
      <input type="text" v-model="insert.quantidade" />

      <button type="submit">Enviar</button>
    </form>

    <div v-for="dado in dados.data" :key="dado.id">
      <p>
        {{ dado.nome }} | {{ dado.quantidade }} |
        <button @click="apagar(dado.id)">X</button>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import api from "@/connection/api.js";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      insert: {},
      dados: {},
    };
  },
  created() {
    axios.get(api.url).then((response) => {
      this.dados = response.data;
    });
  },
  methods: {
    savar() {
      let formData = new FormData();
      formData.append("nome", this.insert.nome);
      formData.append("quantidade", this.insert.quantidade);

      axios.post(api.url, formData, api.headers).then(() => {
        this.insert = {};

        axios.get(api.url).then((response) => {
          this.dados = response.data;
        });
      });
    },
    apagar(id) {
      axios.delete(api.url + "/" + id, "", api.headers).then(() => {
        axios.get(api.url).then((response) => {
          this.dados = response.data;
        });
      });
    },
  },
};
</script>
