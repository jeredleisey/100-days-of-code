<script setup lang="ts">
import { useClipboard } from '@vueuse/core';

const { copy, copied } = useClipboard();

const props = withDefaults(
  defineProps<{
    code?: string;
    language?: string | null;
    filename?: string | null;
    highlights?: Array<number>;
  }>(),
  { code: '', language: null, filename: null, highlights: (): number[] => [] }
);

function fizzBuzz(num: number) {
  return (
    (num % 3 ? '' : 'Fizz') + (num % 5 ? '' : 'Buzz') ||
    'Not divisible by 3 or 5.'
  );
}
</script>

<template>
  <div
    class="group relative border border-slate-600 overflow-hidden rounded-lg bg-gray-900 cursor-default"
    id="code"
  >
    <span
      v-if="filename"
      class="absolute top-0 right-0 px-3 py-2 text-slate-300 text-xs group-hover:text-gray-900 transition-colors"
    >
      {{ filename }}
    </span>

    <slot />
    <span class="absolute right-0 bottom-0 p-2 m-2">
      <button @click="copy(code)" class="pr-1">
        <Icon
          :name="copied ? 'pixelarticons:check' : 'pixelarticons:section-copy'"
          size="18"
          class="opacity-0 text-slate-300 group-hover:opacity-100 transition-opacity"
        />
      </button>
    </span>
  </div>
</template>

<style scoped>
:slotted(pre) {
  display: flex;
  flex: 1 1 0%;
  overflow-x: auto;
  padding: 1rem;
  line-height: 1.625;
  counter-reset: lines;
}

:slotted(pre code) {
  width: 100%;
  display: flex;
  flex-direction: column;
}

:slotted(pre code .line) {
  display: inline-table;
  min-height: 1rem;
}

:slotted(pre code .line::before) {
  counter-increment: lines;
  content: counter(lines);
  width: 1rem;
  margin-right: 1.5rem;
  display: inline-block;
  text-align: left;
  color: rgba(115, 138, 148, 0.4);
}

:slotted(pre code .highlight) {
  background-color: #363b46;
  display: block;
  margin-right: -1em;
  margin-left: -1em;
  padding-right: 1em;
  padding-left: 0.75em;
  border-left: 0.25em solid rgb(255, 141, 141);
}
</style>
