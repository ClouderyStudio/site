<template>
    <header class="z-20 border-b bg-background/90 backdrop-blur sticky">
        <UiContainer class="flex h-16 items-center justify-between lg:h-20">
            <div class="flex items-center gap-10">
                <NuxtLink to="#" class="flex items-center gap-3">
                    <Icon icon="mdi:code" fit="contain" alt="Company Logo" title="Company Logo"
                        class="h-6 rounded object-contain lg:h-8" />
                    <span class="font-semibold lg:text-lg">云术工作室</span>
                </NuxtLink>
                <UiNavigationMenu as="nav" class="hidden items-center justify-start gap-8 lg:flex">
                    <UiNavigationMenuList class="gap-2">
                        <UiNavigationMenuItem>
                            <UiNavigationMenuLink as-child>
                                <UiButton to="#" variant="ghost" size="sm"> 主页</UiButton>
                            </UiNavigationMenuLink>
                        </UiNavigationMenuItem>
                        <template v-for="(data, link, i) in links" :key="i">
                            <UiNavigationMenuItem>
                                <UiNavigationMenuTrigger class="h-9 px-3 text-sm capitalize" :title="link" />
                                <UiNavigationMenuContent>
                                    <div
                                        class="grid grid-cols-1 gap-5 p-4 lg:w-[750px] lg:grid-cols-2 xl:w-[1000px] xl:grid-cols-3">
                                        <div v-for="(item, cat, index) in data" :key="`${cat}-${index}`">
                                            <p class="mb-5 text-sm font-semibold text-primary capitalize">{{ cat }}</p>
                                            <ul class="flex w-full flex-col gap-2">
                                                <li v-for="(child, k) in item" :key="k">
                                                    <UiNavigationMenuLink class="data-active:bg-muted/80" as-child>
                                                        <NuxtLink :to="child.href"
                                                            class="flex flex-row gap-4 rounded-md p-3 transition hover:bg-muted/80 focus-visible:ring-2 focus-visible:ring-ring/50 focus-visible:outline-none">
                                                            <Icon :icon="child.icon"
                                                                class="mt-px h-5 w-5 shrink-0 text-primary" />
                                                            <div class="flex flex-col gap-1.5 leading-none">
                                                                <p class="text-sm font-semibold">{{ child.name }}</p>
                                                                <p class="text-sm text-muted-foreground"
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
            <div class="lg:hidden">
                <UiSheet>
                    <UiSheetTrigger as-child>
                        <UiButton variant="ghost" size="icon-sm">
                            <Icon icon="mdi:menu" class="h-5 w-5" />
                        </UiButton>
                        <UiSheetContent class="w-[90%] p-0">
                            <template #content>
                                <UiSheetTitle class="sr-only" title="Mobile menu" />
                                <UiSheetDescription class="sr-only" description="Mobile menu" />
                                <UiSheetX class="z-20" />

                                <UiScrollArea class="h-full p-5">
                                    <div class="flex flex-col gap-2">
                                        <UiButton variant="ghost" class="justify-start text-base" to="#">主页</UiButton>
                                        <template v-for="(data, link, i) in links" :key="i">
                                            <UiCollapsible>
                                                <UiCollapsibleTrigger as-child>
                                                    <UiButton variant="ghost"
                                                        class="w-full justify-start text-base capitalize *:data-[state=open]:-rotate-180"
                                                        to="#">{{ link }}
                                                        <Icon icon="mdi:chevron-down"
                                                            class="ml-auto size-4 transition" />
                                                    </UiButton>
                                                </UiCollapsibleTrigger>
                                                <UiCollapsibleContent
                                                    class="data-[state=closed]:animate-none data-[state=open]:p-3 data-[state=open]:pt-0">
                                                    <div v-for="(item, cat, index) in data" :key="`${cat}-${index}`"
                                                        class="mt-5">
                                                        <p class="mb-5 text-sm font-semibold text-primary capitalize">
                                                            {{ cat }}
                                                        </p>
                                                        <ul class="flex w-full flex-col gap-2">
                                                            <li v-for="(child, k) in item" :key="k">
                                                                <UiNavigationMenuLink class="data-active:bg-muted/80"
                                                                    as-child>
                                                                    <NuxtLink :to="child.href"
                                                                        class="flex flex-row gap-4 rounded-md p-3 transition hover:bg-muted/80 focus-visible:ring-2 focus-visible:ring-ring/50 focus-visible:outline-none">
                                                                        <Icon :icon="child.icon"
                                                                            class="mt-px h-5 w-5 shrink-0 text-primary" />
                                                                        <div class="flex flex-col gap-1.5 leading-none">
                                                                            <p class="text-sm font-semibold">{{
                                                                                child.name }}</p>
                                                                        </div>
                                                                    </NuxtLink>
                                                                </UiNavigationMenuLink>
                                                            </li>
                                                        </ul>
                                                    </div>
                                                </UiCollapsibleContent>
                                            </UiCollapsible>
                                        </template>

                                        <UiGradientDivider class="my-5" />

                                        <ul class="grid grid-cols-2 gap-x-3 gap-y-5 px-4">
                                            <li v-for="(m, j) in miniLinks" :key="j">
                                                <NuxtLink class="py-2" :to="m.href">{{ m.name }}</NuxtLink>
                                            </li>
                                        </ul>
                                        <UiGradientDivider class="my-5" />
                                        <!-- Social Links Here -->
                                    </div>
                                </UiScrollArea>
                            </template>
                        </UiSheetContent>
                    </UiSheetTrigger>
                </UiSheet>
            </div>
            <div class="hidden items-center gap-3 lg:flex">
                <!-- Socials Links Here -->
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
            /*
            {
                name: "名称",
                description: "描述",
                icon: "mdi:book(图标)",
                href: "链接",
            },
            */
        ],
        游戏: [

        ],
        其他: [

        ],
    },
};
</script>
