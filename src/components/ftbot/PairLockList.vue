<template>
  <div>
    <div class="mb-2">
      <label class="mr-auto h3">Pair Locks</label>
      <b-button class="float-right" size="sm" @click="getLocks">&#x21bb;</b-button>
    </div>
    <div>
      <b-table class="table-sm" :items="currentLocks" :fields="tableFields"> </b-table>
    </div>
  </div>
</template>

<script lang="ts">
import { timestampms } from '@/shared/formatters';
import { BotStoreGetters } from '@/store/modules/ftbot';
import { Lock } from '@/types';
import { Component, Vue } from 'vue-property-decorator';
import { namespace } from 'vuex-class';

const ftbot = namespace('ftbot');

@Component({})
export default class PairLockList extends Vue {
  @ftbot.Action getLocks;

  @ftbot.Getter [BotStoreGetters.currentLocks]!: Lock;

  timestampms = timestampms;

  get tableFields() {
    return [
      { key: 'pair', label: 'Pair' },
      { key: 'lock_end_timestamp', label: 'Until', formatter: 'timestampms' },
      { key: 'reason', label: 'Reason' },
    ];
  }
}
</script>

<style scoped></style>
