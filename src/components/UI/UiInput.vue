<script setup lang="ts">
import { defineProps, defineEmits, computed, watch } from "vue";
import { useField } from "vee-validate";

const props = withDefaults(
  defineProps<{
    modelValue: string | number;
    name: string;
    placeholder?: string;
    type?: string;
    textArea?: boolean;
  }>(),
  {
    textArea: false,
  },
);

const emit = defineEmits(["update:modelValue"]);

const { value, errorMessage, handleBlur, setValue } = useField(props.name);

watch(
  () => props.modelValue,
  (newValue) => {
    setValue(newValue);
  }
);

const inputValue = computed({
  get: () => value.value,
  set: (newValue) => emit("update:modelValue", newValue),
});
</script>

<template>
  <div class="input-wrapper">
    <input
      v-if="!textArea"
      v-model="inputValue"
      :name="name"
      :type="type || 'text'"
      :placeholder="placeholder || ''"
      class="input"
      @blur="handleBlur"
    />
    <textarea
      v-else
      v-model="inputValue"
      :name="name"
      :placeholder="placeholder || ''"
      class="textarea"
      @blur="handleBlur"
    />
    <div v-if="errorMessage" class="error-message">
      {{ errorMessage }}
    </div>
  </div>
</template>

<style>
.input-wrapper {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.input {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  font-family: Arial, "sans-serif";
}

.textarea {
  width: 100%;
  height: 200px;
  padding: 8px 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  resize: none;
  font-family: Arial, "sans-serif";
}

.error-message {
  color: red;
  font-size: 0.875rem;
}
</style>
