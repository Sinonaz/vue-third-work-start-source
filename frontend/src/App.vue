<script setup>
import { AppLayout } from "@/layouts";
import { HomeView } from "@/views";
import rawTasks from "@/mocks/tasks.json";
import users from "@/mocks/users.json";
import { normalizeTask } from "@/common/helpers";
import { STATUSES } from "@/common/constants";

const normalizedTasks = rawTasks.map((task) => normalizeTask(task));
const filters = {
  search: "",
  users: users,
  statuses: STATUSES,
};
</script>

<template>
  <app-layout>
    <home-view :tasks="normalizedTasks" :filters="filters" />
  </app-layout>
</template>

<style lang="scss">
@import "@/assets/scss/app.scss";
</style>
