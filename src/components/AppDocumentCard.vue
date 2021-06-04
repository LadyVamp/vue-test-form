<template>
  <div v-if="data">
    <div class="content">
      <div class="card-header">
        {{ data.name }}
      </div>
      <form @submit.prevent="submit">
        <div class="flex-end">
          <button class="btn primary">Отправить</button>
        </div>
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
      <section v-if="attrs">
        <h4 class="title">Дополнительные характеристики</h4>
        <table>
          <thead>
            <tr>
              <th>№</th>
              <th>Характеристика</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in attrs" :key="item.index">
              <td>{{ index + 1 }}</td>
              <td>
                <span v-if="item.attr_code">{{ item.attr_code }}.</span>
                {{ item.attr_name }}
                <span class="font-bold">: {{ item.attr_value }}</span>
                <span v-if="item.parent_path" class="text-gray-500"
                  >&nbsp;({{ item.parent_path }})</span
                >
              </td>
            </tr>
          </tbody>
        </table>
      </section>
      <section>
        <h4 class="title">Файлы</h4>
        <table>
          <thead>
            <tr>
              <th>№</th>
              <th>Наименование</th>
              <th>Роль файла</th>
              <th>Файл</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in files" :key="item.index">
              <td>{{ index + 1 }}</td>
              <td :class="{ 'pl-4': item.parent_file }">
                {{ item.file_name }}
              </td>
              <td>
                {{ item.file_role }}
              </td>
              <td>
                <a href="{{ item.file_path }}">
                  <img class="icon" src="../assets/download.svg" alt=""
                /></a>
              </td>
            </tr>
          </tbody>
        </table>
      </section>
      <section>
        <app-shipping-containers></app-shipping-containers>
      </section>
    </div>
  </div>
  <div v-else>Нет данных</div>
</template>

<script>
import AppShippingContainers from "./AppShippingContainers";

export default {
  data() {
    return {
      data: null,
      attrs: null,
      files: null,
    };
  },
  created() {
    // Simple GET request using fetch
    fetch(
      "https://gist.githubusercontent.com/LadyVamp/545553debe212fd989ccc6623e9a9fe8/raw/3c5522abe26cd000717d838c9270b5fc21c7000c/files-with-parent.json"
    )
      .then((response) => response.json())
      .then((data) => {
        // console.log(data);
        this.data = data;
        this.attrs = data.attrs;
        this.files = data.files;
        // console.log("files %o", data.files);
      });
  },
  components: {
    AppShippingContainers,
  },
  methods: {
    submit() {
      console.log("submit");
    },
  },
};
</script>

<style scoped></style>
