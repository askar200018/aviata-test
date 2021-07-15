<template>
  <div class="booking">
    <div class="left-panel">
      <MutliSelect
        :options="tariffOptions"
        :selectedOptions="selectedTariffOptions"
        @update-options="filterWithTariffOptions"
      />
      <MutliSelect
        :options="airlinesStates"
        :selectedOptions="selectedAirlines"
        @update-options="filterWithAirlines"
      />
    </div>
    <div class="right-panel">
      <Card
        v-for="flight in flights"
        :key="flight.id"
        :price="flight.price"
        :depDate="flight.itineraries[0][0].dep_date"
        :arrDate="flight.itineraries[0][0].arr_date"
        :carrierSymbol="flight.itineraries[0][0].carrier_name"
      />
    </div>
  </div>
</template>

<script>
const TARIFF_OPTIONS = [
  { id: 'straight', name: 'Только прямые' },
  { id: 'baggage', name: 'Только с багажом' },
  { id: 'returnable', name: 'Только возвратные' },
];
const AIRLINES_STATES = [
  { id: 'KC', name: 'Air Astana' },
  { id: 'HY', name: 'Uzbekistan Airways' },
  { id: 'EK', name: 'Emirates' },
  { id: 'FZ', name: 'Flydubai' },
  { id: 'S7', name: 'S7 Airlines' },
  { id: 'LH', name: 'Lufthansa' },
  { id: 'BT', name: 'Air Baltic' },
  { id: 'CZ', name: 'China Southern Airlines' },
  { id: 'SU', name: 'Aeroflot' },
  { id: 'B2', name: 'Belavia' },
  { id: 'DV', name: 'SCAT Airlines' },
  { id: 'TK', name: 'Turkish Airlines' },
];

import MutliSelect from '../components/MultiSelect.vue';
import Card from '../components/Card.vue';
import { AIRLINES, FLIGHTS } from '../db/data';
export default {
  name: 'Booking',
  components: {
    MutliSelect,
    Card,
  },
  data: function() {
    return {
      airlines: AIRLINES,
      flights: FLIGHTS,
      tariffOptions: TARIFF_OPTIONS,
      selectedTariffOptions: [],
      airlinesStates: AIRLINES_STATES,
      selectedAirlines: AIRLINES_STATES.map((value) => value.id),
    };
  },
  props: {
    msg: String,
  },
  methods: {
    filterWithTariffOptions(options) {
      this.selectedTariffOptions = Object.values(options);
      this.updateFlights();
    },
    filterWithAirlines(options) {
      this.selectedAirlines = Object.values(options);
      this.updateFlights();
    },
    updateFlights() {
      const flightsWithTarifficOptions = FLIGHTS.filter((flight) => {
        if (this.selectedTariffOptions.includes('straight')) {
          if (flight.itineraries[0][0].stops !== 0) {
            return false;
          }
        }
        return true;
      });
      const flightsWithFlights = flightsWithTarifficOptions.filter((flight) => {
        if (this.selectedAirlines.includes(flight.validating_carrier)) {
          return true;
        }
        return false;
      });
      this.flights = flightsWithFlights;
    },
  },
  computed: {},
  mounted() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.booking {
  display: flex;
  justify-content: space-between;
  max-width: 1140px;
  margin: 0 auto;
}
.left-panel {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.right-panel {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
</style>
