<template>
  <div>
    <p>{{ title }}</p>
    <q-input v-model="url" filled type="url" hint="Enter SVG URI" />
    <br />
    <div class="q-gutter-md">
      <q-btn
        v-for="conversionMethod in conversionMethods" :key="conversionMethod.id"
        color="primary"
        :size="'xl'"
        :label="conversionMethod.methodName"
      > <br /></q-btn>
    </div>
  </div>
</template>

<script lang="ts">
import {
  defineComponent,
  PropType,
  computed,
  ref,
  toRef,
  Ref,
} from 'vue';
import { ConversionMethod, Meta } from './models';

function useClickCount() {
  const clickCount = ref(0);
  function increment() {
    clickCount.value += 1
    return clickCount.value;
  }

  return { clickCount, increment };
}

function useDisplayConversionMethod(conversionMethods: Ref<ConversionMethod[]>) {
  const methodCount = computed(() => conversionMethods.value.length);
  return { methodCount };
}

export default defineComponent({
  name: 'ExampleComponent',
  props: {
    title: {
      type: String,
      required: true
    },
    conversionMethods: {
      type: Array as PropType<ConversionMethod[]>,
      default: () => []
    },
    meta: {
      type: Object as PropType<Meta>,
      required: true
    },
    active: {
      type: Boolean
    },
  },
  setup (props) {
    return { url: ref(''), ...useClickCount(), ...useDisplayConversionMethod(toRef(props, 'conversionMethods')) };
  },
});
</script>
