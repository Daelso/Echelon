<template>
  <div class="q-pa-md">
    <q-table
      grid
      title="Officers"
      :rows="rows"
      :columns="columns"
      row-key="name"
      :filter="filter"
      hide-header
      title-class="fake text-center"
      card-class="bg-primary text-secondary text-body1 text-center text-bold"
    >
      <template v-slot:top-right>
        <q-input
          borderless
          dense
          debounce="300"
          v-model="filter"
          placeholder="Search"
          class="text-white"
        >
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
      </template>
    </q-table>
  </div>
  <QuoteSign />
</template>

<style>
.fake {
  color: #daa520;
  font-family: "MachineStd";
  font-size: 40px;
}
</style>

<script>
import { defineComponent, ref } from "vue";
import QuoteSign from "./quoteSign.vue";

const columns = [
  {
    name: "name",
    required: true,
    label: "Name",
    align: "left",
    field: (row) => row.name,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "rank",
    align: "center",
    label: "Rank",
    field: "rank",
    sortable: true,
  },
  { name: "discord", label: "Discord", field: "discord", sortable: true },
];

const rows = [
  {
    name: "[Regiment Leader] [ECH] Congor",
    rank: "Marshal",
    discord: "@thebman",
  },
  {
    name: " [ECH] Uphillwarrior1",
    rank: "Deputy Marshal",
    discord: "@uphillwarrior1",
  },
  {
    name: "[ECH] Colonel Korn",
    rank: "Lance Captain",
    discord: "@clemenade",
  },
  {
    name: "[EU Contact] [ECH] 4naught",
    rank: "Dragoon",
    discord: "@4naught",
  },
];

export default defineComponent({
  name: "officerContact",
  setup() {
    return {
      filter: ref(""),
      columns,
      rows,
    };
  },
  components: { QuoteSign },
});
</script>
