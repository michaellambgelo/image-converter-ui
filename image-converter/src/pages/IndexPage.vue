<template>
  <q-page class="row items-center justify-evenly">
    <example-component
      title="Convert SVG"
      active
      :conversionMethods="conversionMethods"
      :meta="meta"
    ></example-component>
  </q-page>
</template>

<script lang="ts">
import { ConversionMethod, Meta } from 'components/models';
import ExampleComponent from 'components/ExampleComponent.vue';
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'IndexPage',
  components: { ExampleComponent },
  setup () {
    const conversionMethods = ref<ConversionMethod[]>([
      {
        id: 1,
        methodName: 'Convert to JPEG'
      },
      {
        id: 2,
        methodName: 'Convert to PNG'
      },
    ]);
    const meta = ref<Meta>({
      totalCount: 1200
    });
    return { conversionMethods, meta };
  }
});
</script>
