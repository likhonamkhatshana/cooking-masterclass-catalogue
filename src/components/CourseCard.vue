<template>
    <div class="card">
        <h2>{{ title }}</h2>
        <p>
            <strong>Chef:</strong>{{ chef }}
        </p>
        <p>
            <strong>Level:</strong>{{ level}}
        </p>
         <p>
            <strong>Price:</strong>{{ price}}
        </p>
        <p class="status available" v-if="available">
            Available
        </p>
        <p class="status sold-out" v-else>
            Sold Out
        </p>

        <button @click="$emit('save-course')"
        :disabled="!available">
            Save Course
        </button>
    </div>
</template>

<script setup>
    defineProps({
        title: String,
        chef: String,
        level: String,
        price: Number,
        available: Boolean
    })
    
    defineEmits(['save-course'])
</script>