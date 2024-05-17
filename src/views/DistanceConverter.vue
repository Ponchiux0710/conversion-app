<!-- DC view, Rafael Cerdas 2024 -->
<template>
    <div class="converter-container">
        <h1>Conversor de Distancia</h1>
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
            fromUnit: 'metros',
            toUnit: 'kilómetros',
            result: null,
            units: ['metros', 'kilómetros', 'centímetros', 'millas', 'yardas', 'pies', 'pulgadas']
        };
    },
    methods: {
        convert() {
            const conversionRates = {
                metros: 1,
                kilómetros: 0.001,
                centímetros: 100,
                millas: 0.000621371,
                yardas: 1.09361,
                pies: 3.28084,
                pulgadas: 39.3701
            };

            const valueInMeters = this.value * conversionRates[this.fromUnit];
            this.result = valueInMeters / conversionRates[this.toUnit];
        }
    }
};
</script>