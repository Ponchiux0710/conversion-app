<!-- WC view, Rafael Cerdas 2024 -->
<template>
    <div class="converter-container">
        <h1>Conversor de Peso</h1>
        <div class="input-group">
            <input v-model="value" placeholder="Ingrese valor" type="number" />

            <select v-model="toUnit">
                <option v-for="unit in units" :key="unit" :value="unit">{{ unit }}</option>
            </select>
            <select v-model="fromUnit">
                <option v-for="unit in units" :key="unit" :value="unit">{{ unit }}</option>
            </select>
        </div>
        <button @click="convert">Convertir</button>
        <p class="result">Resultado: {{ result }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            value: 0,
            fromUnit: 'kilogramos',
            toUnit: 'gramos',
            result: null,
            units: ['kilogramos', 'gramos', 'toneladas métricas', 'libras', 'onzas']
        };
    },
    methods: {
        convert() {
            const conversionRates = {
                kilogramos: 1,
                gramos: 1000,
                'toneladas métricas': 0.001,
                libras: 2.20462,
                onzas: 35.274
            };

            const valueInKg = this.value * conversionRates[this.fromUnit];
            this.result = valueInKg / conversionRates[this.toUnit];
        }
    }
};
</script>