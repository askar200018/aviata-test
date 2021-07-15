<template>
  <div class="card">
    <div class="card__left">
      <div class="info">
        <div class="info__header">
          <div class="info__logo">
            <img src="../assets/air.svg" alt="Air Astana logo" />
            <p class="info__text">{{ validatingCarrier }}</p>
          </div>
          <div class="info__date">
            <p class="info__day">{{ depDay }}</p>
            <p class="info__time">{{ depTime }}</p>
          </div>
          <div class="info__duration">через Шымкент, 1 ч 50 м</div>
          <div class="info__date">
            <p class="info__day">{{ arrDay }}</p>
            <p class="info__time">{{ arrTime }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="card__right">
      <div class="detail">
        <p class="detail__price">{{ price }} ₸</p>
        <button class="detail__btn">Выбрать</button>
        <p class="detail__text">Цена за всех пассажиров</p>
        <div class="detail__footer">
          <p class="detail__baggage">Нет багажа</p>
          <button class="detail__baggage-btn">+ Добавить багаж</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  computed: {
    depDay: function() {
      return (this.depDate || '').split(' ')[0];
    },
    depTime: function() {
      return (this.depDate || '').split(' ')[1];
    },
    arrDay: function() {
      return (this.arrDate || '').split(' ')[0];
    },
    arrTime: function() {
      return (this.arrDate || '').split(' ')[1];
    },
    validatingCarrier: function() {
      return this.carrierSymbol;
    },
  },
  props: {
    depDate: String,
    arrDate: String,
    carrierName: String,
    price: String,
    carrierSymbol: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.card {
  display: flex;
  width: 880px;
  &__left {
    flex-grow: 1;
    padding: 40px 0 0 20px;
    background-color: #ffffff;
  }
  &__right {
    width: 240px;
    padding: 12px 20px 15px;
    background-color: #f5f5f5;
  }
}
.info {
  &__header {
    display: flex;
    align-items: center;
    gap: 20px;
  }
  &__day,
  &__text {
    font-weight: normal;
    font-size: 12px;
    line-height: 16px;
  }
  &__time {
    font-weight: 600;
    font-size: 24px;
    line-height: 33px;
    color: #202123;
  }
  &__duration {
    font-weight: normal;
    font-size: 12px;
    line-height: 16px;
    color: #ff9900;
  }
}
.detail {
  display: flex;
  flex-direction: column;
  align-items: center;
  &__price {
    margin-bottom: 13px;
    font-family: Arial;
    font-size: 24px;
    line-height: 28px;
    color: #202123;
  }
  &__btn {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 200px;
    height: 40px;
    margin-bottom: 8px;
    font-weight: bold;
    font-size: 18px;
    line-height: 25px;
    color: #ffffff;
    border: none;
    border-radius: 4px;
    background-color: #55bb06;
    outline: none;
    cursor: pointer;
  }
  &__text {
    margin-bottom: 12px;
    font-weight: normal;
    font-size: 12px;
    line-height: 16px;
    color: #707276;
  }
  &__footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
  }
  &__baggage {
    font-weight: normal;
    font-size: 12px;
    line-height: 16px;
    color: #202123;
  }
  &__baggage-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 128px;
    height: 24px;
    font-weight: 600;
    font-size: 12px;
    line-height: 16px;
    color: #5763b3;
    border: none;
    border-radius: 2px;
    background-color: #eaf0fa;
    cursor: pointer;
  }
}
</style>
