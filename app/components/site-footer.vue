<script setup lang="ts"></script>

<template>
  <footer className="border-grid border-t py-6 md:py-0 text-center">
    <div className="container-wrapper">
      <div className="container py-4">
        <div
          className="flex text-balance text-sm leading-loose text-muted-foreground md:text-left justify-center"
        >
          Copyright 2022-{{ new Date().getFullYear() }} Cloudery Studio, All rights reserved.
        </div>
      </div>
    </div>
  </footer>
</template>
