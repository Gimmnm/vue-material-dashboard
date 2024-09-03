<template>
  <div class="content">
    <div class="md-layout">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100" v-for="transaction in transactions" :key="transaction.transaction_id"
      >
        <md-card class="md-card-plain">
          <md-card-header data-background-color="gray">
            <h3 class="title"><strong>{{ transaction.machine_info.name }}</strong></h3>
            <hr>
            <p class="category">
              <span style="float: left; width: 50%;"><strong>Transaction Id</strong>: {{ transaction.transaction_id }}</span>
             <span style="float: right; width: 50%"><strong>Transaction Computing Power</strong>: {{ transaction.computing_power}}</span> 
              <br>

              <span style="float: left; width: 50%;"><strong>CPU</strong>: {{ transaction.machine_info.cpu }}</span>
              <span style="float: right; width: 50%"><strong>GPU</strong>: {{ transaction.machine_info.gpu}}</span> 
              <br>


            </p>
            <hr>
          </md-card-header>
          <md-card-content>
            <SimpleTable_tr :transaction="transaction.bidders"></SimpleTable_tr>
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
      transactions: [{
        transaction_id: "TX1234567890",
        is_sold: false,
        computing_power: "300 TFLOPS",
        machine_info: {
          name: "High-Performance Server X",
          cpu: "Intel Xeon E5-2699 v4",
          gpu: "NVIDIA Tesla V100",
          ram: "256 GB DDR4",
          storage: "4 TB SSD",
          location: "Data Center 1, San Francisco, CA",
          additional_info: "24/7 uptime, energy-efficient cooling system"
        },
        bidders: [
          {
            buyer_id: "BID1001",
            buyer_name: "Company A",
            contact_info: {
              email: "contact@companya.com",
              phone: "+1-555-0100"
            },
            bid_amount: "150,000 USD"
          },
          {
            buyer_id: "BID1002",
            buyer_name: "Company B",
            contact_info: {
              email: "contact@companyb.com",
              phone: "+1-555-0200"
            },
            bid_amount: "155,000 USD"
          },
          {
            buyer_id: "BID1003",
            buyer_name: "Company C",
            contact_info: {
              email: "contact@companyc.com",
              phone: "+1-555-0300"
            },
            bid_amount: "160,000 USD"
          }
        ]
      },
      {
        transaction_id: "TX9876543210",
        is_sold: true,
        computing_power: "500 TFLOPS",
        machine_info: {
          name: "Ultra-Performance Server Z",
          cpu: "AMD EPYC 7742",
          gpu: "NVIDIA A100",
          ram: "512 GB DDR4",
          storage: "8 TB NVMe SSD",
          location: "Data Center 2, New York, NY",
          additional_info: "Redundant power supply, advanced security features"
        },
        bidders: [
          {
            buyer_id: "BID2001",
            buyer_name: "Enterprise X",
            contact_info: {
              email: "info@enterprisex.com",
              phone: "+1-555-1100"
            },
            bid_amount: "200,000 USD"
          },
          {
            buyer_id: "BID2002",
            buyer_name: "TechCorp Y",
            contact_info: {
              email: "sales@techcorpy.com",
              phone: "+1-555-1200"
            },
            bid_amount: "210,000 USD"
          },
          {
            buyer_id: "BID2003",
            buyer_name: "Global Solutions Z",
            contact_info: {
              email: "contact@globalsolutionsz.com",
              phone: "+1-555-1300"
            },
            bid_amount: "220,000 USD"
          }]
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