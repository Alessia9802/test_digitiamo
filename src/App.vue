<template>
  <div id="app">
    <!-- site header -->
    <div id="site_header">
      <h1>Genera una richiesta https</h1>
      <div class="search_box">
        <input type="text" v-model="searchstring" placeholder="Inserisci URL" />
        <button @click="callApi">Cerca</button>
      </div>
    </div>
    <!-- site main -->
    <div id="site_main"></div>
    <!-- site footer -->
    <div id="site_footer"></div>
  </div>
</template>

<script>
//import axios from "axios";
export default {
  name: "App",
  components: {},
  data() {
    return {
      searchstring: "",
      status: "",
      error: "",
      resultsURL: "http://myjson.dit.upm.es/api/bins/goi3/",
    };
  },
  methods: {
    callApi() {
      const request = `${this.searchstring}`;
      console.log(request);

      const url = {
        status: 200,
        method: "GET",
        data: {
          url: this.searchstring,
        },
        response: {},
        request: {},
      };
      console.log(url);

      /* let xhr = new XMLHttpRequest();

      xhr.open("GET", request);

      xhr.send();

      xhr.onload = function () {
        if (xhr.status != 200) {
          // errore HTTP?
          // gestisce l'errore
          alert("Error: " + xhr.status);
          return;
        }

        // ottiene la risposta da xhr.response
      }; */

      /* const statusVerify = function () {
        if (request.status == 200) {
          console.log("success");
        } else {
          console.log("error");
        }
      };
      console.log(statusVerify); */

      const xhttp = new XMLHttpRequest();
      xhttp.open("GET", request);
      xhttp.send();

      xhttp.onreadystatechange = (e) => {
        console.log(xhttp.responseText);
        console.log(e);
      };
      /* axios({
        status: 200,
        method: "GET",
        error: "",
        data: {
          url: request,
          response: {},
          request: {},
        },
      }) */
      /* .then((response) => {
          console.log(response);
          this.response = response.data.results;
        })
        .catch((error) => {
          console.log(error);
          this.error = error;
        }); */
    },
  },
};
</script>

<style></style>
