<script setup>
import { ref ,onMounted} from 'vue'
import { RouterLink } from 'vue-router'
// import axios from 'axios'
import EventService from '@/services/EventService.js'
import EventCard from '@/components/EventCard.vue'
const events = ref(null);

onMounted(() => {
  EventService.getEvents()
     // .get('https://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/events')
      .then((response) => {
        events.value = response.data
        console.log('events',response.data);
      })
      .catch((error) => {
        console.log(error)
      })
})
// const events = ref([
//   {
//     id: 5928101,
//     category: 'animal welfare',
//     title: 'Cat Adoption Day',
//     description: 'Find your new feline friend at this event.',
//     location: 'Meow Town',
//     date: 'January 28, 2022',
//     time: '12:00',
//     petsAllowed: true,
//     organizer: 'Kat Laydee',
//   },
//   {
//     id: 4582797,
//     category: 'food',
//     title: 'Community Gardening',
//     description: 'Join us as we tend to the community edible plants.',
//     location: 'Flora City',
//     date: 'March 14, 2022',
//     time: '10:00',
//     petsAllowed: true,
//     organizer: 'Fern Pollin',
//   },
//   {
//     id: 8419988,
//     category: 'sustainability',
//     title: 'Beach Cleanup',
//     description: 'Help pick up trash along the shore.',
//     location: 'Playa Del Carmen',
//     date: 'July 22, 2022',
//     time: '11:00',
//     petsAllowed: false,
//     organizer: 'Carey Wales',
//   },
// ])
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
