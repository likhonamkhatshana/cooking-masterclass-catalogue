<script setup>
import { ref, computed } from 'vue'
import Header from './components/Header.vue'
import CourseCard from './components/CourseCard.vue'

const wishlistCount = ref(0)

const courses = ref([
   {
    id: 1,
    title: 'Amagwinya',
    chef: 'Chef Likona Mkhatshana',
    level: 'Professional',
    price: 200,
    available: true
  },
  {
    id: 2,
    title: 'Upens',
    chef: 'Chef Annie Spara',
    level: 'Intermediet',
    price: 100,
    available: true
  },
  {
    id: 3,
    title: 'Umngqusho',
    chef: 'Chef Bongiwe Simelane',
    level: 'Professional',
    price: 180,
    available: true
  },
   {
    id: 4,
    title: '7-colours',
    chef: 'Chef Xolelwa Spara',
    level: 'Professional',
    price: 300,
    available: false
  },
])

const saveCourse = () => {
  wishlistCount.value++
}

const showAvailableOnly = ref(false)

const filteredCourses = computed(() => {
  if (showAvailableOnly.value) {
    return courses.value.filter(course => course.available)
  }
  return courses.value
})
</script>

<template>
  <label>
    <input type="checkbox" v-model="showaAilableOnly">
    Available Only
  </label>

  <Header :count="wishlistCount"/>
  <div>
    <CourseCard 
    v-for="course in filteredCourses"
    :key="course.id"
    
    :title="course.title"
    :chef="course.chef"
    :level="course.level"
    :price="course.price"
    :available="course.available"
    @save-course="saveCourse"/>
  </div>
</template>