<template>
  <button
    class=" w-8 h-8 text-gray-800 rounded fill-current hover:text-white hover:bg-blue-700 hover:text-color-white items-center p-2"
    :class="{ 'is-active': isActive ? isActive() : null }"
    @click="action"
    :title="title"
  >
    <svg class="remix h-full w-full">
      <use :xlink:href="`${remixiconUrl}#ri-${icon}`" />
    </svg>
  </button>
</template>

<script>
import remixiconUrl from "remixicon/fonts/remixicon.symbol.svg";

export default {
  props: {
    icon: {
      type: String,
      required: true,
    },

    title: {
      type: String,
      required: true,
    },

    action: {
      type: Function,
      required: true,
    },

    isActive: {
      type: Function,
      default: null,
    },
  },

  data() {
    return {
      remixiconUrl,
    };
  },
};
</script>

<style>
.menu-item {
  color: #0d0d0d;
  border: none;
  background-color: transparent;
  border-radius: 0.4rem;
  padding: 0.25rem;
  margin-right: 0.25rem;
}
</style>
