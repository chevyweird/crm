<script setup lang="ts">
const props = defineProps<{
  title: string;
  value: string;
  hint: string;
}>();
</script>

<template>
  <article class="card">
    <p class="card__title">{{ props.title }}</p>
    <strong class="card__value">{{ props.value }}</strong>
    <span class="card__hint">{{ props.hint }}</span>
  </article>
</template>

<style scoped>
.card {
  background: linear-gradient(135deg, #ffffff, #f7f9fc);
  border: 1px solid #e4ebf3;
  border-radius: 16px;
  padding: 1rem;
  box-shadow: 0 10px 25px rgba(19, 34, 56, 0.06);
}

.card__title {
  margin: 0 0 0.35rem;
  font-size: 0.95rem;
  color: #66758f;
}

.card__value {
  display: block;
  font-size: 1.5rem;
  color: #132238;
  margin-bottom: 0.25rem;
}

.card__hint {
  color: #6b7a90;
  font-size: 0.85rem;
}
</style>
