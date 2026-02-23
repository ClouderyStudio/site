<script setup lang="ts">
  import { CardBody, CardContainer, CardItem } from "@/components/Ui/card-3d";
  import { Icon } from "@iconify/vue";

  import Container from "./components/Ui/Container.vue";
  import ParticlesBg from "./components/Ui/particles-bg/ParticlesBg.vue";
  import SleekLineCursor from "./components/Ui/sleek-line-cursor/SleekLineCursor.vue";

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
    description:
      "我们是一支充满激情的团队，致力于创造卓越的数字体验。从概念到实现，我们专注于每一个细节，为您打造独一无二的作品。",
    services: [
      { icon: "mdi:code", title: "Web开发", desc: "现代响应式网站开发" },
      { icon: "mdi:palette", title: "UI/UX设计", desc: "用户体验与界面设计" },
      { icon: "mdi:globe", title: "全栈开发", desc: "端到端解决方案" },
    ],
    stats: [
      { value: "20+", label: "完成项目" },
      { value: "12+", label: "团队成员" },
      { value: "3", label: "获奖作品" },
    ],
  };

  const projects = [
    {
      id: 1,
      title: "辽阔域名",
      description:
        "辽阔二级域名分发平台，提供免费二级域名注册、DNS解析和API接口，拥有诸如fucku.top、frp.cx等热门域名，适合个人和小型项目使用。",
      tags: ["Domain", "Free", "API", "DNS"],
      icon: "mdi:domain",
      view: "https://lkdns.top",
      image: null,
      category: "Web应用",
    },
    {
      id: 2,
      title: "云术生存战争服务器",
      description:
        "一个趣味生存战争服务器，提供稳定的游戏环境和丰富的玩法，拥有活跃的社区和定期的活动，适合大部分玩家加入。",
      tags: ["SurvivalCraft", "Server", "Community"],
      icon: "mdi:cube",
      view: "https://sc.cldery.com",
      image: null,
      category: "游戏服务",
    },
    {
      id: 3,
      title: "竹像素Minecraft服务器",
      description: "一个现代化、高版本、低延迟的周目制生存服务器。",
      tags: ["Minecraft", "Server", "Modern", "Community"],
      icon: "mdi:minecraft",
      view: "https://mczxs.cn",
      image: null,
      category: "游戏服务",
    },
  ];

  // 项目标签
  const projectTags = ["全部", "Web应用", "游戏服务"];

  // 选中的标签
  const selectedTag = ref(null);

  // 过滤后的项目
  const filteredProjects = computed(() => {
    if (!selectedTag.value) return projects;
    return projects.filter((p) => p.category === selectedTag.value);
  });

  const teamMembers = [
    {
      id: 1,
      name: "柒屹",
      role: "创始人 & 全栈开发",
      bio: "我是柒屹，柒星拱月，屹立不倒。从事互联网事业及网站开发工作，也在搞Java的一些东西。",
      skills: ["Java", "Node.js", "Python", "MongoDB", "Photoshop", "C#", "Maui"],
      avatar: "https://q1.qlogo.cn/g?b=qq&nk=2675256772&s=640",
      socials: [
        { platform: "github", icon: "mdi:github", url: "https://github.com/TulipQiyi" },
        { platform: "youtube", icon: "mdi:youtube", url: "https://space.bilibili.com/1762277941" },
        { platform: "email", icon: "mdi:email", url: "mailto:justqiyi@qq.com" },
      ],
    },
    {
      id: 2,
      name: "云竹",
      role: "创始人 & 全栈开发",
      bio: "这里是云竹，云蒸霞蔚，竹解虚心。对多彩的世界和可爱的你感到好奇，正在尝试从事互联网产品和网站开发相关工作。",
      skills: ["HTML", "CSS", "JavaScript", "Vue.js", "React", "Node.js", "Python"],
      avatar: "https://q1.qlogo.cn/g?b=qq&nk=2457483710&s=640",
      socials: [
        { platform: "github", icon: "mdi:github", url: "https://github.com/yunzhu666" },
        { platform: "youtube", icon: "mdi:youtube", url: "https://space.bilibili.com/526436598" },
        { platform: "email", icon: "mdi:email", url: "mailto:2457483710@qq.com" },
      ],
    },
    {
      id: 3,
      name: "Zero",
      role: "设计师 & 挂群",
      bio: "你知道吗，零是一切的开始。一个虽然没有qqvip但是专门挂群的人。",
      skills: ["Designer", "Photoshop", "Figma", "Adobe XD", "UI/UX Design"],
      avatar: "https://q1.qlogo.cn/g?b=qq&nk=3014786442&s=640",
    },
    {
      id: 4,
      name: "信念",
      role: "服务器管理员",
      bio: "信马由缰，念兹在兹。主管云术生存战争服务器。",
      skills: ["Survival", "Manager", "Communication"],
      avatar: "https://q1.qlogo.cn/g?b=qq&nk=953595252&s=640",
    },
    {
      id: 5,
      name: "C8H806",
      role: "吉祥物",
      bio: "对的，这是一只比较凶的吉祥物，名字叫C8H806，维生素...C8?。负责当吉祥物，lol",
      skills: ["Nothing"],
      avatar: "https://q1.qlogo.cn/g?b=qq&nk=3067315092&s=640",
    },
  ];

  const partners = [
    {
      id: 1,
      name: "PXF我的世界服务器",
      logo: "https://oss.cldery.com/web/site/partners/pxfmc.png",
      icon: "mdi:leaf",
      website: "https://pxfmc.top",
    },
    {
      id: 2,
      name: "云创联跃团队",
      logo: "https://oss.cldery.com/web/site/partners/ycly.webp",
      icon: "mdi:cloud",
      website: "https://ycly.net",
    },
    {
      id: 3,
      name: "辽阔DNS",
      logo: "https://oss.cldery.com/web/site/partners/lkdns.ico",
      icon: "mdi:earth",
      website: "https://lkdns.top",
    },
  ];
</script>

<template>
  <SiteHeader />
  <Container>
    <ClientOnly>
      <SleekLineCursor />
    </ClientOnly>

    <!-- Hero -->
    <section
      className="flex flex-col items-center justify-center text-center py-12 md:py-26 gap-6 relative h-screen inset-0 bg-[url(https://oss.cldery.com/mcweb/assets/images/12.png)] bg-cover bg-center bg-no-repeat bg-fixed"
    >
      <div className="absolute inset-0 bg-white/70 dark:bg-black/45"></div>
      <ParticlesBg
        class="absolute inset-0"
        :quantity="150"
        :ease="150"
        :color="isDark ? '#FFF' : '#000'"
        :staticity="100"
        refresh
      />
      <div className="relative z-10 max-w-3xl mx-auto">
        <div className="max-w-3xl mx-auto">
          <span
            class="pointer-events-none bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-center text-6xl leading-none font-semibold whitespace-pre-wrap text-transparent dark:from-white dark:to-slate-900/10"
          >
            云术工作室
          </span>
          <h2 className="text-xl md:text-2xl mt-4 text-gray-600 dark:text-gray-300 font-light">
            {{ studioInfo.tagline }}
          </h2>
        </div>
        <p className="text-lg max-w-2xl text-gray-600 dark:text-gray-300 mt-6">
          {{ studioInfo.description }}
        </p>
        <div className="mt-8 text-gray-500 dark:text-gray-400 italic max-w-2xl">
          "{{ hitokoto.hitokoto }}" —— {{ hitokoto.from }}
        </div>
      </div>
    </section>

    <UiBlurReveal :delay="0.1" :duration="0.65">
      <section id="smooth" class="container max-w-4xl px-4 py-20 md:mx-auto">
        <div class="text-center lg:text-start" style="opacity: 1; transform: none">
          <h2 className="text-5xl font-bold text-center mb-12 text-gray-800 dark:text-white">
            我们
            <span
              class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-transparent dark:from-white dark:to-slate-900/10"
              >是谁?</span
            >
            <p class="text-sm tracking-widest text-gray-400 md:text-base">`` 了解我们 ``</p>
          </h2>
          <div class="space-y-6 text-lg leading-relaxed text-gray-300 max-md:text-base">
            <p>
              <span
                class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-3xl font-semibold text-transparent dark:from-white dark:to-slate-900/10"
                >云术工作室</span
              >
              是由云竹团队与魔术团队于2022年合并成立的协作组织，
              <br />
              <br />
              我们专注于<span
                class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-3xl font-semibold text-transparent dark:from-white dark:to-slate-900/10"
                >前后端开发 </span
              >和
              <span
                class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-3xl font-semibold text-transparent dark:from-white dark:to-slate-900/10"
                >游戏服务</span
              >领域。
            </p>
            我们的目标是：
            <ul class="list-inside list-disc pl-4">
              <li>构建高质量的开源项目</li>
              <li>促进技术交流与协作</li>
              <li>创造有价值的开发者工具、文档和游戏服务</li>
            </ul>
            <p>欢迎支持或加入我们，一起推动技术创新和社区发展！</p>
          </div>
        </div>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-4xl mx-auto text-center pt-8">
          <div
            v-for="stat in studioInfo.stats"
            className="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm p-6 rounded-xl shadow-lg"
          >
            <UiGlowingEffect
              :spread="40"
              :glow="true"
              :disabled="false"
              :proximity="50"
              :inactive-zone="0.01"
              :border-width="2"
            />
            <div className="text-3xl font-bold text-blue-600 dark:text-blue-400">
              {{ stat.value }}
            </div>
            <div className="text-gray-600 dark:text-gray-300 mt-2">{{ stat.label }}</div>
          </div>
        </div>
      </section>

      <hr class="mx-auto w-[90%] border-gray-700" />

      <!-- Service -->
      <section className="py-24 max-w-4xl mx-auto">
        <h2 className="text-5xl font-bold text-center mb-12 text-gray-800 dark:text-white">
          我们的
          <span
            class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-transparent dark:from-white dark:to-slate-900/10"
            >服务</span
          >
          <p class="text-sm tracking-widest text-gray-400 md:text-base">`` 为您做些什么 ``</p>
        </h2>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div
            v-for="service in studioInfo.services"
            className="bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm p-6 rounded-xl shadow-lg hover:shadow-xl transition-shadow duration-300 border border-gray-200 dark:border-gray-700"
          >
            <UiGlowingEffect
              :spread="40"
              :glow="true"
              :disabled="false"
              :proximity="50"
              :inactive-zone="0.01"
              :border-width="2"
            />
            <div className="text-blue-500 dark:text-blue-400 mb-4 flex justify-center">
              <Icon class="text-5xl" v-bind:icon="service.icon" />
            </div>
            <h3 className="text-xl font-semibold text-center mb-2 text-gray-800 dark:text-white">
              {{ service.title }}
            </h3>
            <p className="text-gray-600 dark:text-gray-300 text-center">{{ service.desc }}</p>
          </div>
        </div>
      </section>

      <hr class="mx-auto w-[90%] border-gray-700" />

      <!-- Team Members -->
      <section className="py-24 max-w-6xl mx-auto">
        <h2 className="text-5xl font-bold text-center mb-12 text-gray-800 dark:text-white">
          核心
          <span
            class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-transparent dark:from-white dark:to-slate-900/10"
            >成员</span
          >
          <p class="text-sm tracking-widest text-gray-400 md:text-base">`` 遇见我们的团队 ``</p>
        </h2>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div
            v-for="member in teamMembers"
            :key="member.id"
            class="group relative overflow-hidden rounded-xl border border-gray-200 bg-white/80 backdrop-blur-sm transition-all duration-300 hover:-translate-y-2 hover:shadow-xl dark:border-gray-700 dark:bg-gray-800/80"
          >
            <UiGlowingEffect
              :spread="40"
              :glow="true"
              :disabled="false"
              :proximity="50"
              :inactive-zone="0.01"
              :border-width="2"
            />

            <div class="relative h-48 overflow-hidden">
              <div v-if="member.avatar" class="h-full w-full">
                <img :src="member.avatar" :alt="member.name" class="h-full w-full object-cover" />
              </div>
              <div
                class="absolute inset-0 flex items-center justify-center gap-4 bg-black/60 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
              >
                <a
                  v-for="social in member.socials"
                  :key="`bottom-${social.platform}`"
                  :href="social.url"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-gray-500 transition-colors hover:text-blue-600 dark:text-gray-400 dark:hover:text-blue-400"
                  :title="social.platform"
                >
                  <Icon :icon="social.icon" class="h-5 w-5" />
                </a>
                <p v-if="!member.socials" class="text-sm text-gray-400 italic">暂无社交链接</p>
              </div>
            </div>

            <div class="p-6 text-center">
              <h3 className="text-xl font-semibold text-gray-800 dark:text-white mb-1">
                {{ member.name }}
              </h3>
              <p className="text-sm text-blue-600 dark:text-blue-400 mb-3">
                {{ member.role }}
              </p>
              <p className="text-sm text-gray-600 dark:text-gray-300 line-clamp-3">
                {{ member.bio }}
              </p>
              <div class="mt-3 flex flex-wrap justify-center gap-2">
                <span
                  v-for="skill in member.skills"
                  class="rounded-full bg-blue-100 px-2 py-1 text-xs text-blue-800 dark:bg-blue-900/30 dark:text-blue-200"
                >
                  {{ skill }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <hr class="mx-auto w-[90%] border-gray-700" />

      <!-- Projects -->
      <section className="py-24 max-w-6xl mx-auto">
        <h2 className="text-5xl font-bold text-center mb-12 text-gray-800 dark:text-white">
          <span
            class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-transparent dark:from-white dark:to-slate-900/10"
            >项目</span
          >
          展示
          <p class="text-sm tracking-widest text-gray-400 md:text-base">`` 我们的各类项目 ``</p>
        </h2>

        <ClientOnly>
          <div class="mb-10 flex flex-wrap justify-center gap-3">
            <button
              v-for="tag in projectTags"
              :key="tag"
              @click="selectedTag = tag === '全部' ? null : tag"
              class="rounded-full px-4 py-2 text-sm font-medium transition-all duration-300"
              :class="[
                selectedTag === tag || (tag === '全部' && !selectedTag)
                  ? 'bg-blue-600 text-white shadow-lg shadow-blue-500/30'
                  : 'bg-gray-100 text-gray-600 hover:bg-gray-200 dark:bg-gray-800 dark:text-gray-300 dark:hover:bg-gray-700',
              ]"
            >
              {{ tag }}
            </button>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <CardContainer v-for="project in filteredProjects" :key="project.id" class="group">
              <CardBody
                class="group/card relative size-auto rounded-xl border border-black/10 bg-gray-50 p-6 transition-all duration-500 hover:scale-[1.02] sm:w-95 dark:border-white/20 dark:bg-gray-800/80 dark:hover:shadow-2xl dark:hover:shadow-emerald-500/[0.1]"
              >
                <CardItem
                  :translate-z="80"
                  class="relative mb-4 h-48 w-full overflow-hidden rounded-lg"
                >
                  <div
                    v-if="project.image"
                    class="h-full w-full bg-cover bg-center transition-transform duration-700 group-hover/card:scale-110"
                    :style="{ backgroundImage: `url(${project.image})` }"
                  />
                  <div
                    v-else
                    class="flex h-full w-full items-center justify-center bg-linear-to-br from-blue-500/20 to-purple-600/20 dark:from-blue-500/10 dark:to-purple-600/10"
                  >
                    <Icon
                      :icon="project.icon || 'mdi:code-brackets'"
                      class="text-6xl text-gray-400 dark:text-gray-600"
                    />
                  </div>

                  <div
                    class="absolute inset-0 flex items-center justify-center bg-black/50 opacity-0 transition-opacity duration-300 group-hover/card:opacity-100"
                  >
                    <a
                      class="rounded-full bg-white/20 px-3 py-1 text-sm font-medium text-white backdrop-blur-sm"
                      :href="project.view"
                    >
                      点击查看详情
                    </a>
                  </div>
                </CardItem>

                <CardItem
                  :translate-z="50"
                  class="mb-2 line-clamp-1 text-xl font-bold text-neutral-600 dark:text-white"
                >
                  {{ project.title }}
                </CardItem>

                <CardItem
                  as="p"
                  translate-z="60"
                  class="mt-2 line-clamp-2 min-h-[40px] text-sm text-neutral-500 dark:text-neutral-300"
                >
                  {{ project.description }}
                </CardItem>

                <!-- 技术标签 -->
                <CardItem :translate-z="70" class="mt-4">
                  <div class="flex flex-wrap gap-2">
                    <span
                      v-for="tag in project.tags"
                      className="px-3 py-1 bg-blue-100 dark:bg-blue-900/30 text-blue-800 dark:text-blue-200 rounded-full text-xs font-medium border border-blue-200 dark:border-blue-800/50"
                    >
                      {{ tag }}
                    </span>
                  </div>
                </CardItem>

                <CardItem
                  :translate-z="60"
                  class="mt-4 flex items-center gap-4 text-xs text-gray-500 dark:text-gray-400"
                >
                  <div v-if="project.stars" class="flex items-center gap-1">
                    <Icon icon="mdi:star" class="h-4 w-4 text-yellow-500" />
                    {{ project.stars }}
                  </div>
                  <div v-if="project.forks" class="flex items-center gap-1">
                    <Icon icon="mdi:source-fork" class="h-4 w-4" />
                    {{ project.forks }}
                  </div>
                  <div v-if="project.updated" class="flex items-center gap-1">
                    <Icon icon="mdi:update" class="h-4 w-4" />
                    {{ project.updated }}
                  </div>
                </CardItem>

                <div class="mt-6 flex items-center justify-between">
                  <CardItem
                    v-if="project.branch"
                    :translate-z="30"
                    class="flex items-center gap-1 text-xs text-gray-500 dark:text-gray-400"
                  >
                    <Icon icon="mdi:source-branch" class="h-3 w-3" />
                    {{ project.branch || "main" }}
                  </CardItem>

                  <div class="flex gap-2">
                    <CardItem
                      v-if="project.view"
                      :translate-z="20"
                      :href="project.view"
                      as="a"
                      target="_blank"
                      class="flex items-center gap-1 rounded-lg bg-gray-200 px-3 py-1.5 text-xs font-medium text-gray-700 transition-colors hover:bg-gray-300 dark:bg-gray-700 dark:text-gray-300 dark:hover:bg-gray-600"
                    >
                      <Icon icon="mdi:eye" class="h-3 w-3" />
                      查看
                    </CardItem>

                    <CardItem
                      v-if="project.link"
                      :translate-z="20"
                      :href="project.link"
                      as="a"
                      target="_blank"
                      class="flex items-center gap-1 rounded-lg bg-black px-3 py-1.5 text-xs font-medium text-white transition-colors hover:bg-gray-800 dark:bg-white dark:text-black dark:hover:bg-gray-200"
                    >
                      <Icon icon="mdi:github" class="h-3 w-3" />
                      源码
                    </CardItem>

                    <CardItem
                      v-else
                      :translate-z="20"
                      as="span"
                      class="flex cursor-not-allowed items-center gap-1 rounded-lg bg-gray-100 px-3 py-1.5 text-xs font-medium text-gray-400 dark:bg-gray-800 dark:text-gray-600"
                    >
                      <Icon icon="mdi:lock" class="h-3 w-3" />
                      私有或非开源项目
                    </CardItem>
                  </div>
                </div>
              </CardBody>
            </CardContainer>
          </div>

          <!-- 查看更多项目按钮
          <div class="mt-12 text-center">
            <a
              href="/projects"
              class="inline-flex items-center gap-2 rounded-full bg-gradient-to-r from-blue-600 to-purple-600 px-6 py-3 font-medium text-white shadow-lg shadow-blue-600/25 transition-all duration-300 hover:-translate-y-0.5 hover:from-blue-700 hover:to-purple-700 hover:shadow-xl hover:shadow-purple-600/30"
            >
              <Icon icon="mdi:apps" class="h-5 w-5" />
              查看更多项目
              <Icon
                icon="mdi:arrow-right"
                class="h-5 w-5 transition-transform group-hover:translate-x-1"
              />
            </a>
          </div>
          -->
        </ClientOnly>
      </section>

      <hr class="mx-auto w-[90%] border-gray-700" />

      <!-- CTA -->
      <section className="py-24 text-center max-w-4xl mx-auto">
        <h2 className="text-3xl font-bold mb-6 text-gray-800 dark:text-white">
          准备开始您的项目了吗？或者是...
          <span
            class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-transparent dark:from-white dark:to-slate-900/10"
            >加入我们？</span
          >
          <p class="text-sm tracking-widest text-gray-400 md:text-base">`` 即刻开始 ``</p>
        </h2>
        <p className="text-lg text-gray-600 dark:text-gray-300 mb-8 max-w-2xl mx-auto">
          与我们合作，将您的想法转化为现实。立即联系我们，开始您的数字之旅。
        </p>
        <div className="flex flex-col sm:flex-row gap-4 justify-center">
          <a
            className="rounded-full border border-solid border-transparent transition-colors flex items-center justify-center bg-foreground text-background gap-2 hover:bg-[#383838] dark:hover:bg-[#ccc] font-medium text-sm sm:text-base h-10 sm:h-12 px-6 sm:px-8"
            href="mailto:admin@cldery.com"
          >
            <Icon icon="mdi:mail" className="w-4 h-4" />
            联系我们
          </a>
          <a
            className="rounded-full border border-solid border-black/8 dark:border-white/[.145] transition-colors flex items-center justify-center hover:bg-[#f2f2f2] dark:hover:bg-[#1a1a1a] hover:border-transparent font-medium text-sm sm:text-base h-10 sm:h-12 px-6 sm:px-8"
            href="https://github.com/ClouderyStudio"
            target="_blank"
            rel="noopener noreferrer"
          >
            <Icon icon="mdi:github" className="w-4 h-4" />
            GitHub
          </a>
          <a
            className="rounded-full border border-solid border-black/8 dark:border-white/[.145] transition-colors flex items-center justify-center hover:bg-[#f2f2f2] dark:hover:bg-[#1a1a1a] hover:border-transparent font-medium text-sm sm:text-base h-10 sm:h-12 px-6 sm:px-8"
            href="https://qm.qq.com/q/K7j4gJ22oC"
            target="_blank"
            rel="noopener noreferrer"
          >
            <Icon icon="mdi:qqchat" className="w-4 h-4" />
            QQ群
          </a>
          <a
            className="rounded-full border border-solid border-transparent transition-colors flex items-center justify-center bg-foreground text-background gap-2 hover:bg-[#383838] dark:hover:bg-[#ccc] font-medium text-sm sm:text-base h-10 sm:h-12 px-6 sm:px-8"
            href="https://doc.cldery.com"
            target="_blank"
            rel="noopener noreferrer"
          >
            文档站
          </a>
        </div>
      </section>

      <hr class="mx-auto w-[90%] border-gray-700" />

      <!-- Partners -->
      <section className="py-24 max-w-6xl mx-auto">
        <h2 className="text-5xl font-bold text-center mb-12 text-gray-800 dark:text-white">
          合作
          <span
            class="bg-linear-to-b from-black to-gray-300/80 bg-clip-text text-transparent dark:from-white dark:to-slate-900/10"
            >伙伴</span
          >
          <p class="text-sm tracking-widest text-gray-400 md:text-base">
            `` 与我们携手共进的人们 ``
          </p>
        </h2>

        <div class="flex flex-wrap justify-center gap-6">
          <div
            v-for="partner in partners"
            :key="partner.id"
            class="group w-40 rounded-xl border border-gray-200 bg-white/80 p-4 text-center backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-lg dark:border-gray-700 dark:bg-gray-800/80"
          >
            <a
              :href="partner.website"
              target="_blank"
              rel="noopener noreferrer"
              class="flex flex-col items-center gap-3"
            >
              <div class="flex h-16 w-16 items-center justify-center">
                <img
                  v-if="partner.logo"
                  :src="partner.logo"
                  :alt="partner.name"
                  class="max-h-full max-w-full object-contain grayscale filter transition-all duration-300 group-hover:grayscale-0"
                />
                <Icon
                  v-else
                  :icon="partner.icon"
                  class="text-3xl text-gray-400 transition-colors group-hover:text-gray-600 dark:text-gray-600 dark:group-hover:text-gray-400"
                />
              </div>

              <span class="text-sm font-medium text-gray-700 dark:text-gray-300">
                {{ partner.name }}
              </span>
            </a>
          </div>
        </div>

        <div class="mt-8 flex items-center justify-center gap-8 text-gray-600 dark:text-gray-400">
          <div class="text-center">
            <span class="text-2xl font-bold text-blue-600 dark:text-blue-400"
              >{{ partners.length }}+</span
            >
            <p class="text-sm">合作团队</p>
          </div>
          <div class="h-8 w-px bg-gray-300 dark:bg-gray-700"></div>
          <div class="text-center">
            <span class="text-2xl font-bold text-blue-600 dark:text-blue-400">4+</span>
            <p class="text-sm">成功项目</p>
          </div>
          <div class="h-8 w-px bg-gray-300 dark:bg-gray-700"></div>
          <div class="text-center">
            <span class="text-2xl font-bold text-blue-600 dark:text-blue-400">2+</span>
            <p class="text-sm">长期伙伴</p>
          </div>
        </div>

        <div class="mt-8 text-center">
          <p class="mb-4 text-gray-500 dark:text-gray-400">
            期待与更多优秀的团队合作，共同创造价值
          </p>
          <a
            href="mailto:admin@cldery.com"
            class="group inline-flex items-center gap-2 font-medium text-blue-600 hover:underline dark:text-blue-400"
          >
            <Icon icon="mdi:handshake" class="h-4 w-4 transition-transform group-hover:rotate-12" />
            寻求合作
            <Icon
              icon="mdi:arrow-right"
              class="h-4 w-4 transition-transform group-hover:translate-x-1"
            />
          </a>
        </div>
      </section>
    </UiBlurReveal>
  </Container>
  <SiteFooter />
</template>
