<template>
    <div>
        <h1>Sommatoria</h1>
        <fieldset>
            <legend>{{titolo}}</legend>
            <p>{{sottotitolo}}</p>
            <input type="number" v-model="numeroInserito"
                   @keypress.enter="sommaNumero">
            <button v-on:click="sommaNumero()">Add</button>
        </fieldset>
        <div>
            Totale = <strong>{{totale}}</strong>
        </div>
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
    name: 'Sommatoria',
    props: {
        titolo: String,
        sottotitolo: String,
        numeroIniziale: Number,
        arElencoIniziale: Array,
    },
    data() {
        return {
            elencoNumeri: [],
            numeroInserito: 0,
            totale: 0
        }
    },
    methods: {
        sommaNumero() {

            // Inserisco il numero della maschera in pagina
            this.elencoNumeri.push(parseInt(
                this.numeroInserito
            ));

           //this.totale += parseInt(this.numeroInserito);
           this.numeroInserito = 0;

            this.$root.data.totalone = 66;
        }
    },
    computed: {
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
