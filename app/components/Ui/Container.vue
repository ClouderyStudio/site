<template>
  <Primitive
    data-slot="container"
    :class="styles({ class: props.class })"
    v-bind="forwarded"
  >
    <slot />
  </Primitive>
</template>

<script lang="ts" setup>
  import { Primitive } from "reka-ui";
  import type { PrimitiveProps } from "reka-ui";
  import type { HTMLAttributes } from "vue";

  const props = withDefaults(
    defineProps<
      PrimitiveProps & {
        /** Custom class(es) to add to the element */
        class?: HTMLAttributes["class"];
        /** Whether to constrain the width of the container */
      }
    >(),
    {
      as: "div",
    }
  );

  const forwarded = reactiveOmit(props, "class");

  const styles = tv({
    base: "mx-auto w-full"
  });
</script>
