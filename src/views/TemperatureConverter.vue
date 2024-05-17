<!-- TC view, Rafael Cerdas 2024 -->
<template>
    <div class="converter-container">
        <h1>Conversor de Temperatura</h1>
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
            fromUnit: 'Celsius',
            toUnit: 'Fahrenheit',
            result: null,
            units: ['Celsius', 'Kelvin', 'Fahrenheit']
        };
    },
    methods: {
        convert() {
            if (this.fromUnit === this.toUnit) {
                this.result = this.value;
            } else {
                let valueInCelsius;

                if (this.fromUnit === 'Celsius') {
                    valueInCelsius = this.value;
                } else if (this.fromUnit === 'Fahrenheit') {
                    valueInCelsius = (this.value - 32) * 5 / 9;
                } else if (this.fromUnit === 'Kelvin') {
                    valueInCelsius = this.value - 273.15;
                }

                if (this.toUnit === 'Celsius') {
                    this.result = valueInCelsius;
                } else if (this.toUnit === 'Fahrenheit') {
                    this.result = valueInCelsius * 9 / 5 + 32;
                } else if (this.toUnit === 'Kelvin') {
                    this.result = valueInCelsius + 273.15;
                }
            }
        }
    }
};
</script>