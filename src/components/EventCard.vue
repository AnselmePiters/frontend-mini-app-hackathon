<template>
  <div class="card mb-3" style="border-radius: 10px">
    <div class="row g-0">
      <div class="col-4">
        <img
          :src="image"
          alt="Event image"
          class="img-fluid rounded-start"
          style="height: 100%; object-fit: cover"
        />
      </div>
      <div class="col-8">
        <div class="card-body">
          <h5 class="card-title text-primary mb-1">{{ title }}</h5>
          <p class="card-text text-secondary small">
            {{ description }}
          </p>
          <p class="card-text text-muted small">{{ date }}</p>
          <button class="btn btn-primary btn-sm">Ticket</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

export default defineComponent({
  name: 'EventCard',
  props: {
    image: {
      type: String as PropType<string>,
      required: true,
    },
    title: {
      type: String as PropType<string>,
      required: true,
    },
    description: {
      type: String as PropType<string>,
      required: true,
    },
    date: {
      type: String as PropType<string>,
      required: true,
    },
  },
})
</script>

<style scoped>
.card-title {
  font-size: 1rem;
}
</style>
