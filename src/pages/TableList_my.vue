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
            <p v-show="1===2">{{ machines[0].Name }}</p>
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
      machines: [],
    };
  },
  created() {
    this.$axios.get('/api/v1/listresources')
      .then(response => {
        this.machines = JSON.parse(response.data.data);
        console.log(this.machines);
      })
      .catch(error => {
        console.error('Error fetching users:', error);
      });
  },

};
</script>
<style scoped>
  hr {
    border: none; /* 移除默认边框 */
    height: 2px; /* 设置线条高度 */
    background-color: #333; /* 设置颜色 */
  }
</style>
