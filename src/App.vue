<!-- APP vue, Rafael Cerdas 2024 -->
<template>
    <div id="app">
        <!-- Navigation -->
        <nav>
            <router-link to="/distance" class="nav-link">Conversor de Distancia</router-link>
            <router-link to="/temperature" class="nav-link">Conversor de Temperatura</router-link>
            <router-link to="/weight" class="nav-link">Conversor de Peso</router-link>
        </nav>
        <router-view />
    </div>
</template>


<script>
export default {
    name: 'App'
};
</script>
