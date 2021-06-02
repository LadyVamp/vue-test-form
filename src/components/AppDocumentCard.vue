<template>
  <h2 v-if="data">{{ data.name }}</h2>
  <div class="content">
    <form class="card bg-gray-50" v-if="data">
      <div class="flex-container">
        <div class="mr-5">
          <div class="form-control">
            <label for="">Номер</label>
            <input type="text" v-model="data.num" />
          </div>
          <div class="form-control">
            <label for="">Дата регистрации</label>
            <input type="text" v-model="data.reg_date" />
          </div>
          <div class="form-control">
            <label for="">Срок хранения в ЦХЭД, год (лет)</label>
            <input type="number" min="0" v-model="data.save_period" />
          </div>
        </div>
        <div class="mr-5">
          <div class="form-control">
            <label for="">Источник</label>
            <input type="text" v-model="data.source_name" />
          </div>
          <div class="form-control">
            <label for="">Идентификатор ЭД в источнике</label>
            <input type="text" v-model="data.source_ed_id" />
          </div>
        </div>
      </div>
    </form>
    <section class="card">
      <h3>Дополнительные характеристики</h3>
    </section>
    <section class="card">
      <h3>Файлы</h3>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: null,
    };
  },
  created() {
    // Simple GET request using fetch
    fetch(
      "https://gist.githubusercontent.com/LadyVamp/bed9499391bb8286d047bc966fdba4bc/raw/feee121c0d5ad23295e279b79c94736b1925ac74/test-data1"
    )
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        this.data = data;
      });
  },
  components() {},
};
</script>

<style scoped>
</style>
