<template>
    <div class="character-list">
        <h1 class="rick-and-morty-title">Personajes de Rick y Morty</h1>

        <SearchFilters :searchQuery="searchQuery" :statusFilter="statusFilter"
            @update:searchQuery="searchQuery = $event" @update:statusFilter="statusFilter = $event" />

        <div v-if="characters.length === 0" class="loading">
            Cargando personajes...
        </div>

        <div class="characters-grid">
            <div v-for="character in characters" :key="character.id" class="character-card">
                <img :src="character.image" :alt="character.name" />
                <p class="character-name">{{ character.name }}</p>
                <p class="character-status">Status: {{ character.status }}</p>
            </div>
        </div>

        <div class="pagination">
            <CustomButton @click="fetchCharacters(prevPage)" :disabled="!prevPage">
                Anterior
            </CustomButton>
            <CustomButton @click="fetchCharacters(nextPage)" :disabled="!nextPage">
                Siguiente
            </CustomButton>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchFilters from './SearchFilters.vue';
import CustomButton from './CustomButton.vue';

export default {
    components: {
        SearchFilters,
        CustomButton
    },
    data() {
        return {
            characters: [],
            nextPage: null,
            prevPage: null,
            searchQuery: '',
            statusFilter: '',
            apiUrl: 'https://rickandmortyapi.com/api/character'
        };
    },
    mounted() {
        this.fetchCharacters(this.apiUrl);
    },
    methods: {
        async fetchCharacters(url) {
            try {
                const response = await axios.get(url, {
                    params: {
                        name: this.searchQuery,
                        status: this.statusFilter,
                    },
                });
                this.characters = response.data.results;
                this.nextPage = response.data.info.next;
                this.prevPage = response.data.info.prev;
            } catch (error) {
                console.error('Error fetching characters:', error);
            }
        },
        applyFilters() {
            this.fetchCharacters(this.apiUrl);
        },
    },
    watch: {
        searchQuery() {
            this.applyFilters();
        },
        statusFilter() {
            this.applyFilters();
        }
    }
};
</script>



<style scoped>
.character-list {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
    background: linear-gradient(to bottom, #1a1a1a, #0a0a0a);
    min-height: 100vh;
}

.rick-and-morty-title {
    font-family: 'Creepster', cursive;
    text-align: center;
    font-size: 48px;
    margin-bottom: 30px;
    color: #39ff14;
    text-shadow:
        0 0 5px #fff,
        0 0 10px #fff,
        0 0 15px #fff,
        0 0 20px #39ff14,
        0 0 35px #39ff14,
        0 0 40px #39ff14,
        0 0 50px #39ff14,
        0 0 75px #39ff14;
}

.characters-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    gap: 20px;
}

.character-card {
    background-color: #2a2a2a;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(57, 255, 20, 0.5);
    transition: transform 0.3s, box-shadow 0.3s;
    text-align: center;
    padding: 15px;
    width: 200px;
    margin: 10px;
    border: 2px solid #39ff14;
}

.character-card:hover {
    transform: scale(1.05);
    box-shadow: 0 0 30px rgba(57, 255, 20, 0.8);
}

.character-card img {
    width: 100%;
    height: auto;
    border-radius: 50%;
    transition: transform 0.3s;
    border: 3px solid #00b5cc;
}

.character-card img:hover {
    transform: scale(1.1);
}

.character-name {
    margin-top: 10px;
    font-weight: bold;
    color: #00b5cc;
}

.character-status {
    color: #39ff14;
}

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

.pagination {
    margin-top: 20px;
    display: flex;
    justify-content: center;
}

button {
    padding: 10px 15px;
    margin: 0 10px;
    background-color: #2a2a2a;
    color: #39ff14;
    border: 2px solid #39ff14;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s ease;
}

button:disabled {
    background-color: #1a1a1a;
    border-color: #666;
    color: #666;
    cursor: not-allowed;
}

button:hover:not(:disabled) {
    background-color: #39ff14;
    color: #000;
}

.loading {
    text-align: center;
    color: #39ff14;
    font-size: 24px;
    margin-top: 50px;
}

@media (max-width: 768px) {
    .characters-grid {
        flex-direction: column;
        align-items: center;
    }

    .character-card {
        width: 80%;
        max-width: 300px;
    }

    .search-filters {
        flex-direction: column;
        align-items: center;
    }

    input[type="text"],
    select {
        width: 100%;
        max-width: 300px;
    }

    button {
        margin: 10px 5px;
    }
}

@media (max-width: 480px) {
    .rick-and-morty-title {
        font-size: 36px;
    }

    .character-card {
        width: 90%;
    }

    .pagination {
        flex-direction: column;
    }

    button {
        width: 100%;
        margin-bottom: 10px;
    }
}
</style>