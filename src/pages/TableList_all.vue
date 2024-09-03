<template>
  <div class="content">
    <div class="md-layout">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100" >
        <md-card class="md-card-plain">
          <md-card-header data-background-color="gray">
            <h3 class="title"><strong>All Resources </strong></h3>
          </md-card-header>
          <hr>
          <md-card-content>
            <SimpleTable_my :machines="machines"></SimpleTable_my>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
import SimpleTable_my from "../components/Tables/SimpleTable_my.vue";

export default {
  components: {
    SimpleTable_my,
  },

  data() {
    return {
      machines: [{
        name: "testmachine1",
        id: 123456,
        state: "正常",
        register_date: "2024-08-31 12:42:12",
        expiration_date: "2024-09-01 00:56:12",
      },{
        name: "testmachine2",
        id: 654321,
        state: "正常",
        register_date: "2024-08-31 12:42:12",
        expiration_date: "2024-09-01 00:56:12",
      },
      {
        name: "testmachine3",
        id: 123456,
        state: "正常",
        register_date: "2024-08-31 12:42:12",
        expiration_date: "2024-09-01 00:56:12",
      },{
        name: "testmachine4",
        id: 654321,
        state: "正常",
        register_date: "2024-08-31 12:42:12",
        expiration_date: "2024-09-01 00:56:12",
      },
      {
        name: "testmachine5",
        id: 123456,
        state: "正常",
        register_date: "2024-08-31 12:42:12",
        expiration_date: "2024-09-01 00:56:12",
      },{
        name: "testmachine6",
        id: 654321,
        state: "正常",
        register_date: "2024-08-31 12:42:12",
        expiration_date: "2024-09-01 00:56:12",
      }]
    };
  }

};
</script>
<style scoped>
  hr {
    border: none; /* 移除默认边框 */
    height: 2px; /* 设置线条高度 */
    background-color: #333; /* 设置颜色 */
  }
</style>