<template>
    <div>
        <h1>Sommatoria</h1>
        <fieldset>
            <legend>{{titolo}}</legend>
            <p>{{sottotitolo}}</p>

            <!-- 
                @keypress.enter="sommaNumero"
                alla pressione del tasto enter viene invocata 
                la funzione "sommaNumero" definita nel nodo
                "methods"
            -->
            <input type="number" 
                    v-model="numeroInserito"
                    @keypress.enter="sommaNumero">

            <!--
                all'evendo "click" sul bottone viene
                invocata la funzione "sommaNumero" definita nel nodo
                "methods"
            -->
            <button v-on:click="sommaNumero()">Add</button>
        </fieldset>
        <div>
            Totale = <strong>{{totale}}</strong>
        </div>
        <!--
            Visualizzo il risultato della computed propery
        -->
        <div>{{sommatoria}}</div>
        <ul>
            <li v-for="numero in elencoNumeri" v-bind:key="numero">
                {{numero}}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    // --- Nome del componente
    name: 'Sommatoria',

    // --- Recupero dei parametri inviati al componente
    props: {
        titolo: String,
        sottotitolo: String,
        numeroIniziale: Number,
        arElencoIniziale: Array,
    },

    // --- Dati trattati dal componente
    data() {
        return {
            elencoNumeri: [],
            numeroInserito: 0,
            totale: 0
        }
    },

    // --- Metodi utilizzati dal componente
    methods: {

        // --- Effettua la somma tra due numeri
        sommaNumero() {

            // Inserisco il numero della maschera in pagina
            this.elencoNumeri.push(parseInt(
                this.numeroInserito
            ));


            this.numeroInserito = 0;

            // --- Qui comunichiamo con una property del componente "parent"
            // --- questo non è il corretto approccio !!!!
            this.$root.data.totalone = 66;
        }
    },
    computed: {
        // --- Definisco la computed property 
        // --- https://vuejs.org/v2/guide/computed.html#Basic-Example

        // --- Ogni volta che nel metodo "sommaNumero", avviene il .push
        // --- sull'array (o ogni qualvolta avviene una modifica su questo array "this.elencoNumeri")
        // --- viene invocata la funzione
        sommatoria() {
            let totale=0;

            this.elencoNumeri.map(
                    (numero) => {
                        totale += numero
                    }
                );
            return totale
        }
    },

    mounted() {
        this.numeroInserito = this.numeroIniziale;
    },

    beforeMount() {

    }
}

</script>

<style scoped></style>
