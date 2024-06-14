<script setup>
import { createClient } from '@supabase/supabase-js'
const supabase = createClient('https://gwzpmebibriyvqjtlaan.supabase.co', 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imd3enBtZWJpYnJpeXZxanRsYWFuIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MTE0NzIzNDYsImV4cCI6MjAyNzA0ODM0Nn0.3LXCdJZMckFZqpbYzy4pZmJe82xBNh_neKyimnlea48')
const countries = ref([])

async function getCountries() {
  const { data } = await supabase.from('images').select()
  countries.value = data
}

onMounted(() => {
  getCountries()
})
</script>

<template>
    <p v-for="country in countries" :key="country.id">
      <img :src=country.src :alt=country.alt style="height: 200px; width: 200px; object-fit: cover;">
    </p>
</template>