<template>
  <div>
    <header>
      <div class="container">
        <div class="row">
          <div class="col-md-2 col-2">
            <img src="../assets/logo.png" alt class="logo" />
          </div>
          <div class="col-md-8 col-8">
            <h1 class="title-1">Coronavírus na cidade de Patos-PB</h1>
            <p class="text-center">Última atualização: {{date}}</p>
          </div>
          <div class="col-md-2 col-2">
            <img src="../assets/bandeira.png" alt class="logo" />
          </div>
        </div>
      </div>
    </header>
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <h2
            class="title-2"
          >Fonte: Secretarias de Saúde das Unidades Federativas, dados tratados por Álvaro Justen e colaboradores/Brasil.IO.</h2>
          <h2 class="title-2">
            Brasil.IO: boletins epidemiológicos da COVID-19 por município por dia, disponível em:
            <a
              href="https://brasil.io/dataset/covid19/"
              target="_blank"
            >https://brasil.io/dataset/covid19/</a>
            (última atualização: {{date}}, acesso em {{current_date}}).
          </h2>
        </div>
      </div>
      <div class="row">
        <Card titulo="Número de casos confirmados" v-bind:info="confirmed" />
        <Card titulo="Número de mortes" v-bind:info="deaths" />
        <Card titulo="População estimada" v-bind:info="estimated_population_2019" />
        <Card titulo="Taxa de mortalidade (mortes / confirmados)" v-bind:info="death_rate" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "../components/Card";

export default {
  name: "Home",
  components: {
    Card
  },
  data() {
    return {
      confirmed: "",
      deaths: "",
      estimated_population_2019: "",
      death_rate: "",
      date: "",
      current_date: ""
    };
  },
  mounted() {
    this.currentDate();
    this.getData();
  },
  methods: {
    currentDate() {
      var data = new Date(),
        dia = data.getDate().toString(),
        diaF = dia.length == 1 ? "0" + dia : dia,
        mes = (data.getMonth() + 1).toString(),
        mesF = mes.length == 1 ? "0" + mes : mes,
        anoF = data.getFullYear();
      this.current_date = diaF + "-" + mesF + "-" + anoF;
    },
    getData() {
      axios
        .get(
          "https://brasil.io/api/dataset/covid19/caso/data/?is_last=True&city_ibge_code=2510808"
        )
        .then(response => {
          if (response.data.results.length > 0) {
            const patos = response.data.results[0];

            this.confirmed = patos.confirmed;
            this.deaths = patos.deaths;
            this.estimated_population_2019 = patos.estimated_population_2019;
            this.death_rate = patos.death_rate;
            this.date = patos.date
              .split("-")
              .reverse()
              .join("-");
          }
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<style>
header {
  background-color: #fff;
  box-shadow: rgba(0, 0, 0, 0.059216) 0px 4px 9px 0px;
  margin-bottom: 20px;
}
.logo {
  width: 70px;
  margin: 20px auto;
  display: block;
}
h1.title-1 {
  text-align: center;
  font-size: 33px;
  padding-top: 18px;
}
h2.title-2 {
  font-size: 20px;
}

@media (max-width: 768px) {
  .logo {
    width: 33px;
    margin: 30px auto;
  }
  h1.title-1 {
    text-align: center;
    font-size: 17px;
    padding-top: 13px;
  }
  p {
    font-size: 11px;
  }
  h2.title-2 {
    font-size: 11px;
  }
}
</style>
