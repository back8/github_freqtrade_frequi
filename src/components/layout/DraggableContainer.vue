<template>
  <div class="card h-100 w-100 overflow-auto">
    <div class="drag-header card-header">
      {{ header }}
    </div>
    <div class="card-body h-100 w-100">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';

@Component({})
export default class DraggableContainer extends Vue {
  @Prop({ required: true, type: String }) header!: string;
}
</script>

<style scoped>
.card-header {
  padding: 0.25rem 0.5rem;
}
.card-body {
  /* Padding should be controled by the contained element */
  padding: 0;
}
</style>
