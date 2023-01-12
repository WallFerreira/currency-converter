<template>
    <div class="conversor">
        <h2>{{ moedaA }} para {{ moedaB }}</h2>
        <input id="input-text" type="text" pattern="[^0-9]+" v-model="moedaA_value" v-bind:placeholder="moedaA">
        <input id="input-button" type="button" value="Converter" @click="converter">

        <h2> {{ moedaB_value }} {{ moedaB }}</h2>
    </div>
</template>
<script>
export default {
    name: "Conversor",
    props: ["moedaA", "moedaB"],

    data() {
        return {
            moedaA_value: "",
            moedaB_value: 0,
        };
    },

    methods: {

        converter() {
            let token = "2316|SWwJXQPgM3qS3PGuBKuGI8h4liI8DWg7"
            let de_para = this.moedaA + "_" + this.moedaB;
            let url = `https://api.invertexto.com/v1/currency/${de_para}?token=${token}`

            fetch(url)
                .then((res) => {
                    console.log(res)

                    if (res.status == 200 && this.moedaA_value > 0) {
                        return res.json()
                    }
                })
                .then(json => {
                    let cotacao = json[de_para].price;
                    this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2)
                })
                .catch(() => alert(`Digite um número válido`))
        }
    },
}
</script>
<style>
.conversor {
    max-width: 300px;
    padding: 20px;
    margin-bottom: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

#input-button{
    margin-left: 5px;
}

#input-text{
    align-items: center;
}
</style>