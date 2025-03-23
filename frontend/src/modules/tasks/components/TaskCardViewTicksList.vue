<script setup>
import AppIcon from "@/common/components/AppIcon.vue";

defineProps({
  disabled: {
    type: Boolean,
    default: false,
  },
  ticks: {
    type: Array,
    default: () => [],
  },
});

const emits = defineEmits(["createTick", "updateTick", "removeTick"]);

const updateTick = function (tick, property, value) {
  const tickCopy = Object.assign({}, tick);
  tickCopy[property] = value;
  emits("updateTick", tickCopy);
};
</script>

<template>
  <div class="task-card__check-list">
    <h4 class="task-card__title">
      Чек-лист

      <!--Кнопка создания новой подзадачи-->
      <button
        v-if="!$props.disabled"
        type="button"
        class="task-card__plus"
        @click="$emit('createTick')"
      />
    </h4>
    <!--Список подзадач-->
    <ul v-if="ticks.length" class="task-card__list">
      <li
        v-for="tick in ticks"
        :key="tick.id || tick.uuid"
        class="task-card__item"
      >
        <div class="task-card__checkbox">
          <label class="checkbox">
            <div class="checkbox__icon">
              <input
                type="checkbox"
                name="remember"
                :checked="tick.done"
                @click="updateTick(tick, 'done', !tick.done)"
              />
              <span />
            </div>
            <div class="checkbox__label">
              <input
                v-if="!disabled"
                type="text"
                name="checkbox_name"
                :value="tick.text"
                max="64"
                placeholder="Введите текст пункта"
                @change="updateTick(tick, 'text', $event.target.value)"
              />
              <span v-else>{{ tick.text }}</span>
            </div>
          </label>
        </div>

        <div
          class="task-card__icons"
          :class="{ 'task-card__icons--hidden': disabled }"
        >
          <app-icon
            class="icon--trash"
            @click="$emit('removeTick', { uuid: tick.uuid, id: tick.id })"
          />
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss"></style>
