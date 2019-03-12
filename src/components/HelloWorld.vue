<template>
  <div class="hello">

    <h1>Totale Generale: {{recuperoTotalone}}</h1>
    <Sommatoria titolo="Esempio passaggio informazioni al compoenete"
                sottotitolo="Vediamo come recuperare i dati"
                numero-iniziale="55"
    :arElencoIniziale="elencoInizale"></Sommatoria>

    <Sommatoria titolo="Somma di quanti isse ho chiuso du Jire"
                sottotitolo="QUate issue e problematiche ho chiuso oggi si JIra"
                numero-iniziale="0"></Sommatoria>

  </div>
</template>

<script>
import Sommatoria from "./sommatoria";
export default {
  name: 'HelloWorld',
  components: {Sommatoria},
  props: {
    msg: String
  },
  data() {
    return {
      elencoInizale: [34, 65, 89],
      recuperoTotalone: this.$root.totalone,
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
