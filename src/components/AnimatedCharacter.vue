<template>
  <div
    class="animated-character"
    :class="type"
    ref="character"
    :style="characterStyle"
  >
    <template v-if="type === 'paperclip'">
      <img src="@/assets/paper-clip.png" alt="Paperclip" class="paperclip-img" />
      <img src="@/assets/Pupil.svg" alt="Character" class="character-inside" />
    </template>
    <template v-else-if="type === 'idle'">
      <img src="@/assets/Pupil.svg" alt="Idle Character" class="idle-img" />
    </template>
    <template v-else-if="type === 'follow-cursor'">
      <img src="@/assets/Pupil.svg" alt="Follow Character" class="follow-img" />
    </template>
  </div>
</template>

<script>
import { ref, onMounted, onBeforeUnmount, watch } from 'vue';
import gsap from 'gsap';

export default {
  name: 'AnimatedCharacter',
  props: {
    type: {
      type: String,
      default: 'idle', // 'idle', 'follow-cursor', 'paperclip'
    },
    index: {
      type: Number,
      default: 0,
    }
  },
  setup(props) {
    const character = ref(null);
    const characterStyle = ref({});
    let tl = null;
    let followHandler = null;

    onMounted(() => {
      if (props.type === 'paperclip') {
        // Вращение скрепки
        tl = gsap.timeline({ repeat: -1, defaults: { ease: 'power1.inOut' } });
        tl.to(character.value, { rotate: 360, duration: 4 });
      }
      if (props.type === 'idle') {
        // Idle покачивание через CSS (см. стиль)
        // Можно добавить небольшое смещение для разных index
        characterStyle.value = {
          animationDelay: `${props.index * 0.5}s`
        };
      }
      if (props.type === 'follow-cursor') {
        // Следим за мышкой
        followHandler = (e) => {
          const x = e.clientX;
          const y = e.clientY;
          character.value.style.transform = `translate(-50%, -50%) translate(${x}px, ${y}px)`;
        };
        window.addEventListener('mousemove', followHandler);
        // Стартовая позиция
        character.value.style.position = 'fixed';
        character.value.style.left = '0';
        character.value.style.top = '0';
        character.value.style.transform = 'translate(-50%, -50%)';
        character.value.style.pointerEvents = 'none';
      }
    });

    onBeforeUnmount(() => {
      if (tl) tl.kill();
      if (props.type === 'follow-cursor' && followHandler) {
        window.removeEventListener('mousemove', followHandler);
      }
    });

    watch(() => props.type, (newType, oldType) => {
      if (oldType === 'follow-cursor' && followHandler) {
        window.removeEventListener('mousemove', followHandler);
      }
    });

    return { character, characterStyle };
  }
};
</script>

<style scoped>
.animated-character {
  width: 90px;
  height: 90px;
  position: absolute;
  pointer-events: none;
  display: flex;
  align-items: center;
  justify-content: center;
}
.paperclip-img {
  width: 100%;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  z-index: 1;
}
.character-inside {
  width: 40px;
  height: 40px;
  position: absolute;
  left: 50%;
  top: 70%;
  transform: translate(-50%, -50%);
  z-index: 2;
}
.idle-img {
  width: 90px;
  height: 90px;
  animation: idle-bob 2.5s ease-in-out infinite alternate;
}
@keyframes idle-bob {
  0% { transform: translateY(0) rotate(-3deg); }
  100% { transform: translateY(18px) rotate(3deg); }
}
.follow-img {
  width: 90px;
  height: 90px;
}
</style> 