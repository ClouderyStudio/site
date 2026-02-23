<template>
    <header class="fixed w-full top-0 z-50 shadow-sm backdrop-blur">
        <UiContainer class="flex h-16 items-center justify-between lg:h-16 px-20">
            <div class="flex items-center gap-15">
                <NuxtLink to="#" class="flex items-center gap-3">
                    <Icon icon="mdi:code" fit="contain" alt="Logo" title="Logo"
                        class="h-6 rounded object-contain lg:h-8" />
                    <span class="font-semibold lg:text-lg">云术工作室</span>
                </NuxtLink>
                <UiNavigationMenu as="nav" class="hidden items-center justify-start gap-8 lg:flex">
                    <UiNavigationMenuList class="gap-2">
                        <UiNavigationMenuItem>
                            <UiNavigationMenuLink as-child class="px-4">
                                <UiButton to="#" variant="ghost" size="sm">主页</UiButton>
                            </UiNavigationMenuLink>
                        </UiNavigationMenuItem>
                        <template v-for="(data, link, i) in links" :key="i">
                            <UiNavigationMenuItem>
                                <UiNavigationMenuTrigger class="h-9 px-4 text-sm capitalize bg-transparent" :title="link" />
                                <UiNavigationMenuContent>
                                    <div
                                        class="grid grid-cols-1 gap-5 p-4 lg:w-[750px] lg:grid-cols-2 xl:w-[1000px] xl:grid-cols-3">
                                        <div v-for="(item, cat, index) in data" :key="`${cat}-${index}`">
                                            <p class="mb-5 text-sm font-semibold text-primary capitalize">{{ cat }}</p>
                                            <ul class="flex w-full flex-col gap-2">
                                                <li v-for="(child, k) in item" :key="k">
                                                    <UiNavigationMenuLink as-child>
                                                        <NuxtLink :to="child.href"
                                                            class="flex flex-row gap-4 rounded-md p-3 transition focus-visible:ring-2 focus-visible:ring-ring/50 focus-visible:outline-none">
                                                            <Icon :icon="child.icon"
                                                                class="mt-px h-5 w-5 shrink-0 text-primary" />
                                                            <div class="flex flex-col gap-1.5 leading-none">
                                                                <p class="text-sm font-semibold">{{ child.name }}</p>
                                                                <p class="text-sm"
                                                                    v-html="child.description" />
                                                            </div>
                                                        </NuxtLink>
                                                    </UiNavigationMenuLink>
                                                </li>
                                            </ul>
                                        </div>
                                    </div>
                                </UiNavigationMenuContent>
                            </UiNavigationMenuItem>
                        </template>
                    </UiNavigationMenuList>
                </UiNavigationMenu>
            </div>

            <!-- 桌面端社交链接 -->
            <div class="hidden items-center gap-3 lg:flex">
                <NuxtLink v-for="socialLink in socialLinks" :key="socialLink.name" :to="socialLink.href" class="py-2">
                    {{ socialLink.name }}
                </NuxtLink>
            </div>

            <!-- 移动端菜单 -->
            <div class="lg:hidden">
                <UiSheet>
                    <UiSheetTrigger as-child>
                        <UiButton variant="ghost" size="icon-sm">
                            <Icon icon="mdi:menu" class="h-5 w-5" />
                        </UiButton>
                    </UiSheetTrigger>
                    <UiSheetContent class="w-[90%] p-0">
                        <template #content>
                            <UiSheetTitle class="sr-only">Mobile menu</UiSheetTitle>
                            <UiSheetDescription class="sr-only">Mobile navigation menu</UiSheetDescription>
                            <UiSheetX class="z-20" />

                            <UiScrollArea class="h-full p-5">
                                <div class="flex flex-col gap-2">
                                    <UiButton variant="ghost" class="justify-start text-base" to="#">主页</UiButton>
                                    <template v-for="(data, link, i) in links" :key="i">
                                        <UiCollapsible>
                                            <UiCollapsibleTrigger as-child>
                                                <UiButton variant="ghost"
                                                    class="w-full justify-start text-base capitalize" to="#">
                                                    {{ link }}
                                                    <Icon icon="mdi:chevron-down" class="ml-auto size-4 transition-transform ui-expanded:rotate-180" />
                                                </UiButton>
                                            </UiCollapsibleTrigger>
                                            <UiCollapsibleContent>
                                                <div class="pt-2">
                                                    <div v-for="(item, cat, index) in data" :key="`${cat}-${index}`"
                                                        class="mt-5 first:mt-0">
                                                        <p class="mb-3 text-sm font-semibold text-primary capitalize">
                                                            {{ cat }}
                                                        </p>
                                                        <ul class="flex w-full flex-col gap-1">
                                                            <li v-for="(child, k) in item" :key="k">
                                                                <NuxtLink :to="child.href"
                                                                    class="flex flex-row gap-4 rounded-md p-3 transition hover:bg-muted/80 focus-visible:ring-2 focus-visible:ring-ring/50 focus-visible:outline-none">
                                                                    <Icon :icon="child.icon"
                                                                        class="mt-px h-5 w-5 shrink-0 text-primary" />
                                                                    <div class="flex flex-col gap-1.5 leading-none">
                                                                        <p class="text-sm font-semibold">{{ child.name }}</p>
                                                                    </div>
                                                                </NuxtLink>
                                                            </li>
                                                        </ul>
                                                    </div>
                                                </div>
                                            </UiCollapsibleContent>
                                        </UiCollapsible>
                                    </template>

                                    <UiGradientDivider class="my-5" />

                                    <ul class="grid grid-cols-2 gap-x-3 gap-y-5 px-4">
                                        <li v-for="m in miniLinks" :key="m.name">
                                            <NuxtLink class="py-2" :to="m.href">{{ m.name }}</NuxtLink>
                                        </li>
                                    </ul>
                                    <UiGradientDivider class="my-5" />

                                    <ul class="grid grid-cols-2 gap-x-3 gap-y-5 px-4">
                                        <li v-for="social in socialLinks" :key="social.name">
                                            <NuxtLink class="py-2" :to="social.href">{{ social.name }}</NuxtLink>
                                        </li>
                                    </ul>
                                </div>
                            </UiScrollArea>
                        </template>
                    </UiSheetContent>
                </UiSheet>
            </div>
        </UiContainer>
    </header>
</template>

<script lang="ts" setup>
import { Icon } from '@iconify/vue';

const miniLinks = [
    { name: "About us", href: "#" },
    { name: "Press", href: "#" },
    { name: "Careers", href: "#" },
    { name: "Legal", href: "#" },
    { name: "Support", href: "#" },
    { name: "Contact", href: "#" },
    { name: "Sitemap", href: "#" },
    { name: "Cookie settings", href: "#" },
];

const links = {
    云术: {
        开发: [
            {
                 name: "名称",
                 description: "描述",
                 icon: "mdi:book",
                 href: "链接",
            },
        ],
        游戏: [],
        其他: [],
    },
};

const socialLinks = [
    {
        name: "Github",
        href: "https://github.com/ClouderyStudio"
    }
];
</script>