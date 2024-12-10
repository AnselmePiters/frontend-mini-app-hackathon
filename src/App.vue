<template>
  <div class="container-fluid bg-gradient" style="min-height: 100vh; padding-bottom: 4rem">
    <!-- Header -->
    <header class="text-center py-3">
      <!-- <img src="logo.png" alt="Tolewa Event" class="img-fluid" style="max-width: 100px" /> -->
      <h1 class="mt-2 text-primary">Tolewa Event</h1>
      <p class="text-secondary">Découvrez, réservez, vibrez</p>
    </header>

    <!-- Search and Filter -->
    <div class="px-3 mb-3">
      <div class="input-group mb-2">
        <input
          type="text"
          class="form-control"
          placeholder="Rechercher"
          aria-label="Rechercher"
          v-model="searchQuery"
        />
        <button class="btn btn-outline-secondary" type="button">
          <i class="bi bi-search"></i>
        </button>
      </div>
      <div class="d-flex justify-content-between">
        <button class="btn btn-outline-secondary"><i class="bi bi-camera"></i> Scanner</button>
        <button class="btn btn-outline-secondary"><i class="bi bi-funnel"></i> Filtrer</button>
      </div>
    </div>

    <!-- Events List -->
    <div>
      <h2 class="px-3 text-dark">Événements disponibles</h2>
      <div class="px-3">
        <EventCard
          v-for="event in filteredEvents"
          :key="event.id"
          :image="event.image"
          :title="event.title"
          :description="event.description"
          :date="event.date"
        />
      </div>
    </div>

    <!-- Footer Navigation -->
    <nav class="navbar fixed-bottom navbar-light bg-white border-top d-flex justify-content-around">
      <button class="btn btn-link text-primary"><i class="bi bi-house"></i> Accueil</button>
      <button class="btn btn-link text-secondary"><i class="bi bi-cart"></i> Panier</button>
      <button class="btn btn-link text-secondary"><i class="bi bi-ticket"></i> Mes tickets</button>
      <button class="btn btn-link text-secondary">
        <i class="bi bi-question-circle"></i> Aide
      </button>
    </nav>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue'
import EventCard from './components/EventCard.vue'

interface Event {
  id: number
  image: string
  title: string
  description: string
  date: string
}

export default defineComponent({
  name: 'App',
  components: {
    EventCard,
  },
  setup() {
    const searchQuery = ref<string>('')

    const events = ref<Event[]>([
      {
        id: 1,
        image: 'https://via.placeholder.com/150',
        title: 'Name Event 1',
        description: 'Lorem ipsum descriptions Lorem ipsum descriptions',
        date: '11 dec 2024 - 15:00',
      },
      {
        id: 2,
        image: 'https://via.placeholder.com/150',
        title: 'Name Event 2',
        description: 'Lorem ipsum descriptions Lorem ipsum descriptions',
        date: '11 dec 2024 - 15:00',
      },
      {
        id: 3,
        image: 'https://via.placeholder.com/150',
        title: 'Name Event 3',
        description: 'Lorem ipsum descriptions Lorem ipsum descriptions',
        date: '11 dec 2024 - 15:00',
      },
    ])

    const filteredEvents = computed(() =>
      events.value.filter((event) =>
        event.title.toLowerCase().includes(searchQuery.value.toLowerCase()),
      ),
    )

    return {
      searchQuery,
      events,
      filteredEvents,
    }
  },
})
</script>

<style>
.bg-gradient {
  background: linear-gradient(to bottom, #ffdf70, #ff8c94);
}

.navbar button i {
  font-size: 1.5rem;
}

.navbar button {
  font-size: 0.9rem;
}
</style>
