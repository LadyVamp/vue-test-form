<template>
  <div class="card">
    <h2 v-if="data">{{ data.name }}</h2>
    <div class="content">
      <section>
        <h3>Общие характеристики</h3>
        <div v-if="data">
          <p>{{ data.num }}</p>
          <p>{{ data.reg_date }}</p>
          <p>{{ data.source_name }}</p>
          <p>{{ data.source_ed_id }}</p>
          <p>{{ data.save_period }}</p>
        </div>
      </section>
      <section>
        <h3>Дополнительные характеристики</h3>
      </section>
      <section>
        <h3>Файлы</h3>
      </section>
    </div>
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
};
</script>

<style scoped>
</style>
