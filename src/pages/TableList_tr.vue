<template>
  <div class="content">
    <div class="md-layout">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100" >
        <md-card class="md-card-plain">
          <!-- <md-card-header data-background-color="gray"> -->
            <!-- <h3 class="title"><strong> My Resources </strong></h3> -->
            
          <!-- </md-card-header> -->
          <!-- ... -->
          <hr>
          <md-card-content>
            <p v-show="1===2">{{ transactions[0].status }}</p>
            <SimpleTable_tr :transactions="transactions"></SimpleTable_tr>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
import SimpleTable_tr from "../components/Tables/SimpleTable_tr.vue";

export default {
  components: {
    SimpleTable_tr,
  },
  data() {
    return {
      transactions: [],
      timer: null,
    };
  },
  mounted() {
    this.fetchData();
    this.timer = setInterval(this.fetchData, 10000);
  },
  methods: {
    fetchData() {
      console.log("hello");
      console.log(this.transactions)
      this.$axios.get('/api/v1/market/list')
        .then(response => {
          this.transactions = JSON.parse(response.data.data);
        })
        .catch(error => {
          console.error('Error fetching users:', error);
        });
    }
  },
  beforeDestroy() {
    // 清除定时器
    if (this.timer) {
      clearInterval(this.timer);
    }
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
