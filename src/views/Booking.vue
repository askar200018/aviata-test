<template>
  <div class="booking">
    <h1 class="booking__title">Booking vue</h1>
    <div class="left-panel">
      <MutliSelect
        :options="tariffOptions"
        :selectedOptions="selectedTariffOptions"
        @update-options="update"
      />
      <MutliSelect
        :options="airlines"
        :selectedOptions="selectedAirlines"
        @update-options="update"
      />
    </div>
  </div>
</template>

<script>
const TARIFF_OPTIONS = [
  { id: "straight", name: "Только прямые" },
  { id: "baggage", name: "Только с багажом" },
  { id: "returnable", name: "Только возвратные" },
];
const AIRLINES = [
  { id: "KC", name: "Air Astana" },
  { id: "HY", name: "Uzbekistan Airways" },
  { id: "EK", name: "Emirates" },
  { id: "FZ", name: "Flydubai" },
  { id: "S7", name: "S7 Airlines" },
  { id: "LH", name: "Lufthansa" },
  { id: "BT", name: "Air Baltic" },
  { id: "CZ", name: "China Southern Airlines" },
  { id: "SU", name: "Aeroflot" },
  { id: "B2", name: "Belavia" },
  { id: "DV", name: "SCAT Airlines" },
  { id: "TK", name: "Turkish Airlines" },
];

import MutliSelect from "../components/MultiSelect.vue";
export default {
  name: "Booking",
  components: {
    MutliSelect,
  },
  data: function () {
    return {
      tariffOptions: TARIFF_OPTIONS,
      selectedTariffOptions: [],
      airlines: AIRLINES,
      selectedAirlines: AIRLINES.map((value) => value.id),
    };
  },
  props: {
    msg: String,
  },
  methods: {
    update(options) {
      console.log("options in parent", options);
    },
  },
  mounted() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.booking {
  max-width: 1140px;
  margin: 0 auto;
}
.left-panel {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
</style>
