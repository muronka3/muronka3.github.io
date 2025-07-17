<template>
  <div
    class="animated-character"
    :class="type"
    ref="character"
    :style="characterStyle"
  >
    <template v-if="type === 'paperclip'">
      <div class="paperclip-container" ref="paperclip">
        <img src="@/assets/paper-clip.png" alt="Paperclip" class="paperclip-img" />
        <div class="character-inside-container" ref="person">
          <div class="character-inside">
            <img src="@/assets/person.png" alt="Person" class="person-img" />
            <div class="eye eye-left">
              <img src="@/assets/eye_white.svg" class="eye-white" />
              <img src="@/assets/Pupil.svg" class="pupil" />
            </div>
            <div class="eye eye-right">
              <img src="@/assets/eye_white.svg" class="eye-white" />
              <img src="@/assets/Pupil.svg" class="pupil" />
            </div>
          </div>
        </div>
      </div>
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
    const paperclip = ref(null);
    const person = ref(null);
    let tl = null;
    let followHandler = null;

    onMounted(() => {
      if (props.type === 'paperclip') {
        // Явно задаём начальные стили для плавного цикла
        gsap.set(paperclip.value, { rotate: 0 });
        gsap.set(person.value, { top: 200, left: 40 });

        // Четырехтактная анимация: поворот - съезд - поворот - съезд
        tl = gsap.timeline({ repeat: -1, defaults: { ease: 'power1.inOut' } });
        // 1. Поворот скрепки и персонажа на -180° (от 30° до -150°)
        tl.to(paperclip.value, { rotate: -180, duration: 1.2 });
        // 2. Персонаж "съезжает" по диагонали в левый верхний угол (top: 0px, left: 160px)
        tl.to(person.value, { top: 0, left: 160, duration: 0.7 }, '-=0.2');
        // 3. Поворот скрепки и персонажа на -360° (от -150° до -330°)
        tl.to(paperclip.value, { rotate: -360, duration: 1.2 });
        // 4. Персонаж возвращается по диагонали в левый нижний угол (top: 240px, left: 0px)
        tl.to(person.value, { top: 200, left: 40, duration: 0.7 }, '-=0.2');
        // 5. Возврат персонажа в исходное положение (top: 240px, left: 0px)
        tl.to(person.value, { top: 200, left: 40, duration: 0.1 });
        // 6. Плавно возвращаем скрепку к 30° по кратчайшему пути (shortRotation)
        tl.to(paperclip.value, { shortRotation: { rotate: 30 }, duration: 0.5 });
      }
      if (props.type === 'idle') {
        characterStyle.value = {
          animationDelay: `${props.index * 0.5}s`
        };
      }
      if (props.type === 'follow-cursor') {
        followHandler = (e) => {
          const x = e.clientX;
          const y = e.clientY;
          character.value.style.transform = `translate(-50%, -50%) translate(${x}px, ${y}px)`;
        };
        window.addEventListener('mousemove', followHandler);
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

    return { character, characterStyle, paperclip, person };
  }
};
</script>

<style scoped>
.animated-character {
  width: 360px;
  height: 360px;
  position: absolute;
  pointer-events: none;
  display: flex;
  align-items: center;
  justify-content: center;
}
.paperclip-container {
  width: 100%;
  height: 100%;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}
.paperclip-img {
  height: 100%;
  width: auto;
  object-fit: contain;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%) rotate(30deg);
  transform-origin: center center;
  z-index: 1;
}
.character-inside-container {
  position: absolute;
  left: 0px;
  top: 240px;
  /* Старт: левый нижний угол */
  width: 152px;
  height: 152px;
  z-index: 2;
  transition: filter 0.2s;
}
.character-inside {
  width: 100%;
  height: 100%;
  position: relative;
}
.person-img {
  width: 100%;
  height: 100%;
  display: block;
}
.eye {
  position: absolute;
  width: 52px;
  height: 52px;
}
.eye-left {
  left: 0px;
  top: 28px;
}
.eye-right {
  right: 0px;
  top: 28px;
}
.eye-white, .pupil {
  position: absolute;
  left: 0;
  top: 0;
}
.eye-white {
  width: 52px;
  height: 52px;
}
.pupil {
  width: 24px;
  height: 24px;
  left: 16px;
  top: 16px;
}
.idle-img {
  width: 360px;
  height: 360px;
  animation: idle-bob 2.5s ease-in-out infinite alternate;
}
@keyframes idle-bob {
  0% { transform: translateY(0) rotate(-3deg); }
  100% { transform: translateY(72px) rotate(3deg); }
}
.follow-img {
  width: 360px;
  height: 360px;
}
</style> 