<template>
  <div class="card">
    <h2>Документ 1</h2>
    <div class="content">
      <section>
        <h3>Общие характеристики</h3>
        <p>
          <label for="num">Номер</label>
          <input id="num" v-model="num" type="text" name="num"/>
        </p>
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
export default {};
</script>

<style scoped>

</style>
