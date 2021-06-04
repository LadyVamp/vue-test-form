<template>
  <div>
    <h4 class="title">Транспортные контейнеры</h4>
    <table>
      <thead>
        <tr>
          <th>№</th>
          <th>Дата и время формирования</th>
          <th>Статус</th>
          <th>Архив</th>
          <th>Фонд</th>
          <th>Дата и время отправки в ЦХЭД</th>
          <th>Дата окончания действия сертификата подписи</th>
          <th>Файл ЭП</th>
          <th>Файл ТК</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in data" :key="item.index">
          <td>{{ index + 1 }}</td>
          <td>{{ item.form_date }}</td>
          <td>{{ item.status[0].value }}</td>
          <td>{{ item.archieve[0].short_name }}</td>
          <td>{{ item.fund[0].value }}</td>
          <td>{{ item.send_date }}</td>
          <td>{{ item.sign_end_date }}</td>
          <td>
            <a href="{{ item.ep_path }}">
              <img class="icon" src="../assets/download.svg" alt=""
            /></a>
          </td>
          <td>
            <a href="{{ item.tk_path }}">
              <img class="icon" src="../assets/download.svg" alt=""
            /></a>
          </td>
        </tr>
      </tbody>
    </table>
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
    fetch(
      "https://gist.githubusercontent.com/LadyVamp/b528949c90b12e05c86c302bda1c89c0/raw/4cd14dba04fc233b2f43cf57637cd0b6a5936ba8/transport-containers.json"
    )
      .then((response) => response.json())
      .then((data) => {
        this.data = data.tk;
      });
  },
};
</script>

<style lang="scss" scoped></style>
