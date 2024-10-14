<template>
    <div class="search-filters">
        <input type="text" :value="searchQuery" @input="$emit('update:searchQuery', $event.target.value)"
            placeholder="Buscar por nombre" />
        <select :value="statusFilter" @change="$emit('update:statusFilter', $event.target.value)">
            <option value="">Filtrar por estado</option>
            <option value="alive">Vivo</option>
            <option value="dead">Muerto</option>
            <option value="unknown">Desconocido</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'SearchFilters',
    props: {
        searchQuery: String,
        statusFilter: String
    }
}
</script>

<style scoped>
.search-filters {
    margin-bottom: 20px;
    display: flex;
    justify-content: center;
    gap: 15px;
}

input[type="text"],
select {
    padding: 10px;
    border-radius: 5px;
    border: 2px solid #39ff14;
    width: 200px;
    box-sizing: border-box;
    background-color: #2a2a2a;
    color: #fff;
}

@media (max-width: 768px) {
    .search-filters {
        flex-direction: column;
        align-items: center;
    }

    input[type="text"],
    select {
        width: 100%;
        max-width: 300px;
    }
}
</style>