<template>
    <div class="card" style="width: 18rem;">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <p class="card-text">{{ content }}</p>
            <a :href="link" class="btn btn-primary">{{ nameButon || "Enviar" }}</a>
        </div>
    </div>
</template>

<script setup lang="ts">
defineProps<{
    title: string,
    content: string,
    link: string,
    nameButon?: string
}>();

</script>

<style scoped></style>