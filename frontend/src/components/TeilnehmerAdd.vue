<template>
  <html>
    <nav>
          <input type="text" class="searchbar" placeholder="Suche ...">
          <a href="/#/Verwaltung/" >Alle Veranstaltungen</a>
          <a href="/#/Veranstaltung/" >Veranstaltung erstellen </a>
          <a href="/#/Teilnehmer/" >Alle Teilnehmer</a>
          <a href="/#/TeilnehmerAdd/" class="selected">Teilnehmer erstellen</a>
        </nav>
    <main>
    <h1> Microservice 1 :)</h1>
    </main>
  </html>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Teilnehmer',
  data () {
    return {
      user: [],
      errors: []
    };
  },
  created () {
    var id = parseFloat(this.$route.query.id);
    axios.get('http://localhost:8088/api/user/' + id)
    .then(response => {
      this.user = response.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  },
  methods: {
    kill (event) {
      event.target.parentElement.parentElement.remove();
    }
  }
}

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

