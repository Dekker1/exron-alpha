<script setup>
  import { ref } from 'vue';
  import RosterSelector from '@/components/RosterSelector.vue';
  import RosterTable from '@/components/RosterTable.vue';
  import { useRosterStore } from '@/stores/roster';
  import { OptimizedRoster } from '@/services/OptimizedRoster';
  
  const loading = ref(false);
  const rosterStore = useRosterStore();

  const load = () => {
      loading.value = true;
      setTimeout(() => {
          loading.value = false;
          rosterStore.addRoster(OptimizedRoster.getData());
      }, 2000);
  };
</script>

<template>
  <div class="home">
    <!-- <h1>Roster view</h1> -->
  </div>
  
  
  <div class="formgrid grid">
    <div class="field col">
      <h1>Select your roster here:</h1>
      <RosterSelector></RosterSelector>
    </div>
    <div class="field col">
      <h3>Here's the roster you selected</h3>
      <RosterTable></RosterTable>
    </div>
  </div>
  <div class="card flex justify-content-center">
      <Button type="button" label="Generate New Roster?" icon="pi pi-search" :loading="loading" @click="load" />
  </div>
</template>