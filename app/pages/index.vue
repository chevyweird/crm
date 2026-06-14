<script setup lang="ts">
import { ref } from "vue"; 

definePageMeta({
  ssr: false,
});

const stats = [
  { title: "Новых сделок", value: "24", hint: "За последние 7 дней" },
  { title: "Активных клиентов", value: "132", hint: "Сейчас в работе" },
  { title: "Конверсия", value: "18%", hint: "По результатам месяца" },
];

const tasks = ref([
  { id: 1, name: "Проверить договоры", done: false },
  { id: 2, name: "Позвонить клиенту", done: true },
  { id: 3, name: "Подготовить отчет", done: false },
]);

function toggleTask(id: number) {
  tasks.value = tasks.value.map((task) =>
    task.id === id ? { ...task, done: !task.done } : task,
  );
}
</script>

<template>
  <main class="page">
    <section class="hero">
      <div>
        <p class="eyebrow">CRM dashboard</p>
        <h1>Управляйте клиентами и задачами в одном месте</h1>
        <p class="hero__text">
          Простая панель для контроля продаж, клиентов и текущих дел.
        </p>
      </div>
      <button class="primary-btn">Добавить сделку</button>
    </section>

    <section class="stats-grid">
      <CrmCard
        v-for="item in stats"
        :key="item.title"
        :title="item.title"
        :value="item.value"
        :hint="item.hint"
      />
    </section>

    <section class="panel">
      <div class="panel__header">
        <h2>Сегодняшние задачи</h2>
        <span>3 задачи</span>
      </div>

      <ul class="task-list">
        <li v-for="task in tasks" :key="task.id" class="task-item">
          <label>
            <input
              type="checkbox"
              :checked="task.done"
              @change="toggleTask(task.id)"
            />
            <span :class="{ done: task.done }">{{ task.name }}</span>
          </label>
        </li>
      </ul>
    </section>
  </main>
</template>

<style scoped>
.page {
  min-height: 100vh;
  padding: 2rem;
  background: linear-gradient(135deg, #f4f7fb, #eef4ff);
  color: #132238;
}

.hero {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
  background: white;
  border-radius: 24px;
  padding: 2rem;
  margin-bottom: 1.5rem;
  box-shadow: 0 18px 40px rgba(19, 34, 56, 0.08);
}

.eyebrow {
  margin: 0 0 0.5rem;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  font-size: 0.76rem;
  color: #5f78a8;
  font-weight: 700;
}

.hero h1 {
  margin: 0 0 0.5rem;
  font-size: clamp(1.6rem, 2.5vw, 2.4rem);
}

.hero__text {
  margin: 0;
  color: #67809a;
  max-width: 560px;
}

.primary-btn {
  border: none;
  background: #2f6fed;
  color: white;
  padding: 0.8rem 1.2rem;
  border-radius: 999px;
  cursor: pointer;
  font-weight: 600;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.panel {
  background: white;
  border-radius: 24px;
  padding: 1.25rem 1.5rem;
  box-shadow: 0 18px 40px rgba(19, 34, 56, 0.08);
}

.panel__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.task-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: grid;
  gap: 0.75rem;
}

.task-item label {
  display: flex;
  align-items: center;
  gap: 0.7rem;
  cursor: pointer;
}

.done {
  text-decoration: line-through;
  color: #93a2b6;
}

@media (max-width: 700px) {
  .hero {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
