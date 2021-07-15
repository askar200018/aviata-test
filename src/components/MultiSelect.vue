<template>
  <div class="options">
    <h3 class="options__title">Опции тарифа</h3>
    <div class="options__list">
      <label v-for="option in options" :key="option.id" class="options__label">
        <input
          type="checkbox"
          :value="option.id"
          v-model="checkedOptions"
          v-on:change="filterMedia"
        />
        <div class="options__checkbox"></div>
        <p class="options__text">{{ option.name }}</p>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MutliSelect',
  data: function() {
    return {
      checkedOptions: [],
    };
  },
  props: {
    selectedOptions: Array,
    options: Array,
  },
  methods: {
    filterMedia() {
      this.$emit('update-options', this.checkedOptions);
    },
  },
  mounted() {
    this.checkedOptions = this.selectedOptions;
  },
  watch: {
    selectedOptions: function(newVal) {
      this.checkedOptions = newVal;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.options {
  display: inline-block;
  width: 240px;
  background-color: #f5f5f5;
  padding: 12px 12px;
  &__title {
    margin-bottom: 12px;
    font-size: 14px;
    font-weight: bold;
    line-height: 20px;
    color: #202123;
  }
  &__label {
    display: flex;
    align-items: center;
    gap: 12px;
    height: 32px;
    cursor: pointer;
  }
  &__text {
    font-size: 12px;
    font-weight: normal;
    line-height: 16px;
    color: #202123;
  }
  input {
    display: none;
    &:checked ~ .options__checkbox {
      background: url('../assets/checked.svg') center no-repeat;
      background-color: #55bb06;
      border-color: #55bb06;
    }
  }
  &__checkbox {
    display: inline-block;
    width: 12px;
    height: 12px;
    border: 1px solid #b9b9b9;
    border-radius: 2px;
    background-color: #ffffff;
  }
}
</style>
