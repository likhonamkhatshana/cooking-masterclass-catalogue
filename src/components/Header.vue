<template>
    <header class="header">
        <h1>Cooking Masterclass</h1>
        <div class="wishlist">
            wishlist: {{ count }}
        </div>
    </header>
</template>

<script setup>
    defineProps({
        count: Number
    })
</script>