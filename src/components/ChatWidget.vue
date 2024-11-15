<template>
  <!-- Chat Frame -->
  <div v-show="isChatVisible" :style="chatFrameStyles">
    <iframe :src="chatUrl" :width="`${frameWidth}`" :height="`${frameHeight}`" title="Chat Widget" />
  </div>

  <!-- Chat Button -->
  <div @click="toggleChatVisibility" class="chat-button-container">
    <div class="chat-button" :style="chatButtonStyles" @mouseenter="isHovered = true" @mouseleave="isHovered = false">
      <!-- SVG Icon -->
      <svg viewBox="0 0 24 24" width="32" height="32">
        <path fill="currentColor"
          d="M12 3c5.5 0 10 3.58 10 8s-4.5 8-10 8c-1.24 0-2.43-.18-3.53-.5C5.55 21 2 21 2 21c2.33-2.33 2.7-3.9 2.75-4.5C3.05 15.07 2 13.13 2 11c0-4.42 4.5-8 10-8" />
      </svg>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, PropType, CSSProperties } from 'vue';

const props = defineProps({
  chatUrl: {
    type: String as PropType<string>,
    required: true,
  },
  buttonColor: {
    type: String as PropType<string>,
    default: '#e74266',
  },
  buttonHoverColor: {
    type: String as PropType<string>,
    default: '#d6365d',
  },
  buttonSize: {
    type: String as PropType<string>,
    default: '64px',
  },
  frameWidth: {
    type: [String, Number] as PropType<string | number>,
    default: 400,
  },
  frameHeight: {
    type: [String, Number] as PropType<string | number>,
    default: 600,
  },
});

const isChatVisible = ref(false);
const isHovered = ref(false);

const toggleChatVisibility = () => {
  isChatVisible.value = !isChatVisible.value;
};

const chatFrameStyles = computed<CSSProperties>(() => ({
  position: 'fixed',
  bottom: `calc(${props.buttonSize} + 25px)`,
  right: '1rem',
  zIndex: 999,
  display: isChatVisible.value ? 'block' : 'none',
}));

// Chat button styles using template literals and props
const chatButtonStyles = computed<CSSProperties>(() => ({
  backgroundColor: isHovered.value ? `${props.buttonHoverColor}` : `${props.buttonColor}`,
  width: `${props.buttonSize}`,
  height: `${props.buttonSize}`,
  borderRadius: '50%',
  display: 'flex',
  alignItems: 'center',
  justifyContent: 'center',
  color: '#fff',
  transition: 'transform 0.15s ease, background-color 0.15s ease',
  transform: isHovered.value ? 'scale(1.05)' : 'scale(1)',
}));
</script>

<style scoped>
.chat-button-container {
  position: fixed;
  bottom: 1rem;
  right: 1rem;
  z-index: 9999;
  cursor: pointer;
}

iframe {
  border: none;
  overflow: hidden;
  transform-origin: bottom right;
}
</style>
