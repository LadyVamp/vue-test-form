<template>
  <div class="card">
    <h2>Документ 1</h2>
    <div class="content">
      <section>
        <h3>Общие характеристики</h3>
        <div v-if="data">
          <p>{{ data.num }}</p>
          <p>{{ data.reg_date }}</p>
          <p>{{ data.source[0].source_name }}</p>
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
      "https://gist.githubusercontent.com/LadyVamp/bed9499391bb8286d047bc966fdba4bc/raw/36fe37536fe6a41279f2e9390c82e4dae48a82de/test-data1"
    )
      .then((response) => response.json())
      // .then((data) => (this.data = data));
      .then((data) => {
        console.log(data);
        this.data = data;
      });
  },
};
</script>

<style scoped>
</style>
