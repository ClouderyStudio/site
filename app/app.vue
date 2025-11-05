<script setup lang="ts">
import ParticlesBg from './components/Ui/particles-bg/ParticlesBg.vue';
import { Icon } from "@iconify/vue";

async function getHitokoto() {
  try {
    const response = await fetch("https://v1.hitokoto.cn");
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("获取一言数据失败:", error);
    return { hitokoto: "代码改变世界", from: "程序员" };
  }
}

const hitokoto = await getHitokoto();

const studioInfo = {
  name: "云术工作室",
  tagline: "创意与技术的完美结合",
  description: "我们是一支充满激情的团队，致力于创造卓越的数字体验。从概念到实现，我们专注于每一个细节，为您打造独一无二的作品。",
  services: [
    { icon: "mdi:code", title: "Web开发", desc: "现代响应式网站开发" },
    { icon: "mdi:palette", title: "UI/UX设计", desc: "用户体验与界面设计" },
    { icon: "mdi:globe", title: "全栈开发", desc: "端到端解决方案" },
  ],
  stats: [
    { value: "20+", label: "完成项目" },
    { value: "12+", label: "团队成员" },
    { value: "3", label: "获奖作品" },
  ]
};
</script>

<template>
  <div className="min-h-screen pb-20">
    <SiteHeader class="relative" />
    <!--
    <ClientOnly>
      <SleekLineCursor />
    </ClientOnly>
    -->
    <ParticlesBg class="absolute inset-0" :quantity="150" :ease="150" :color="isDark ? '#FFF' : '#000'" :staticity="100"
      refresh />
    <UiBlurReveal :delay="0.2" :duration="0.75">
      <!-- Hero -->
      <section className="flex flex-col items-center text-center py-12 md:py-26 gap-6">
        <div className="max-w-3xl mx-auto">
          <span
            class="pointer-events-none whitespace-pre-wrap bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-center text-6xl font-semibold leading-none text-transparent dark:from-white dark:to-slate-900/10">
            云术工作室
          </span>
          <h2 className="text-xl md:text-2xl mt-4 text-gray-600 dark:text-gray-300 font-light"> {{ studioInfo.tagline }}
          </h2>
        </div>
        <p className="text-lg max-w-2xl text-gray-600 dark:text-gray-300 mt-6">
          {{ studioInfo.description }}
        </p>
        <div className="mt-8 text-gray-500 dark:text-gray-400 italic max-w-2xl">
          "{{ hitokoto.hitokoto }}" —— {{ hitokoto.from }}
        </div>
      </section>

      <!-- Stats -->
      <section className="py-12">
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-4xl mx-auto text-center">
          <div v-for="(stat) in studioInfo.stats"
            className="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm p-6 rounded-xl shadow-lg">
            <UiGlowingEffect :spread="40" :glow="true" :disabled="false" :proximity="50" :inactive-zone="0.01"
              :border-width="2" />
            <div className="text-3xl font-bold text-blue-600 dark:text-blue-400">{{ stat.value }}</div>
            <div className="text-gray-600 dark:text-gray-300 mt-2">{{ stat.label }}</div>
          </div>
        </div>
      </section>

      <!-- Service -->
      <section className="py-34 max-w-4xl mx-auto">
        <h2 className="text-3xl font-bold text-center mb-12 text-gray-800 dark:text-white">
          我们的服务
        </h2>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="service in studioInfo.services"
            className="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm p-6 rounded-xl shadow-lg hover:shadow-xl transition-shadow duration-300 border border-gray-200 dark:border-gray-700">
            <UiGlowingEffect :spread="40" :glow="true" :disabled="false" :proximity="50" :inactive-zone="0.01"
              :border-width="2" />
            <div className="text-blue-500 dark:text-blue-400 mb-4 flex justify-center">
              <Icon class="text-5xl" v-bind:icon="service.icon" />
            </div>
            <h3 className="text-xl font-semibold text-center mb-2 text-gray-800 dark:text-white">{{ service.title }}
            </h3>
            <p className="text-gray-600 dark:text-gray-300 text-center">{{ service.desc }}</p>
          </div>
        </div>
      </section>

      <!-- CTA -->
      <section className="py-16 text-center max-w-4xl mx-auto">
        <h2 className="text-3xl font-bold mb-6 text-gray-800 dark:text-white">
          准备开始您的项目了吗？
        </h2>
        <p className="text-lg text-gray-600 dark:text-gray-300 mb-8 max-w-2xl mx-auto">
          与我们合作，将您的想法转化为现实。立即联系我们，开始您的数字之旅。
        </p>
        <div className="flex flex-col sm:flex-row gap-4 justify-center">
          <a className="rounded-full border border-solid border-transparent transition-colors flex items-center justify-center bg-foreground text-background gap-2 hover:bg-[#383838] dark:hover:bg-[#ccc] font-medium text-sm sm:text-base h-10 sm:h-12 px-6 sm:px-8"
            href="mailto:contact@cloudery.com">
            <Icon icon="mdi:mail" className="w-4 h-4" />
            联系我们
          </a>
          <a className="rounded-full border border-solid border-black/[.08] dark:border-white/[.145] transition-colors flex items-center justify-center hover:bg-[#f2f2f2] dark:hover:bg-[#1a1a1a] hover:border-transparent font-medium text-sm sm:text-base h-10 sm:h-12 px-6 sm:px-8"
            href="https://github.com/ClouderyStudio" target="_blank" rel="noopener noreferrer">
            <Icon icon="mdi:github" className="w-4 h-4" />
            GitHub
          </a>
          <a className="rounded-full border border-solid border-transparent transition-colors flex items-center justify-center bg-foreground text-background gap-2 hover:bg-[#383838] dark:hover:bg-[#ccc] font-medium text-sm sm:text-base h-10 sm:h-12 px-6 sm:px-8"
            href="https://doc.cldery.com" target="_blank" rel="noopener noreferrer">
            文档站
          </a>
        </div>
      </section>
    </UiBlurReveal>
  </div>
</template>
