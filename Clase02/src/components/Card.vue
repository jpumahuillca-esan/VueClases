<template>
    <div class="card" style="width: 18rem;">
        <img class="card-img-top" src="..." alt="Card image cap">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <p class="card-text">{{ content }}</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
    </div>
    <div>

    </div>
</template>

<script setup lang="ts">
defineProps<{
    id?: number,
    title?: string,
    content?: string,
}>();
</script>

<style scoped></style>