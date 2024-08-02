<template>
    <div class="centered-text" :style="gradientStyle">
      Hello Word
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  
  const gradientColors = ['red', 'orange', 'yellow', 'green', 'cyan', 'blue', 'violet'];
  const gradientStyle = ref({});
  
  const generateGradient = () => {
    const randomColors = [];
    while (randomColors.length < 3) {
      const color = gradientColors[Math.floor(Math.random() * gradientColors.length)];
      if (!randomColors.includes(color)) {
        randomColors.push(color);
      }
    }
    return `linear-gradient(90deg, ${randomColors.join(', ')})`;
  };
  
  const applyGradient = () => {
    const gradient = generateGradient();
    gradientStyle.value = {
      backgroundImage: gradient,
      '-webkit-background-clip': 'text',
      color: 'transparent',
      backgroundSize: '200% 200%',
      animation: 'gradientAnimation 10s ease-in-out infinite',
    };
  };
  
  onMounted(() => {
    applyGradient();
    setInterval(applyGradient, 3000); // 每10秒更新一次渐变
  });
  </script>
  
  <style scoped>
  @keyframes gradientAnimation {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }
  
  .centered-text {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    font-size: 50px;
    font-weight: bold;
    background-size: 200% 200%; /* 保证渐变动画从左到右平滑过渡 */
  }
  </style>