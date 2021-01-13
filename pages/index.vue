<template>
  <div class="container">
    <select v-model="selectedView">
      <option v-for="(cat, index) in categories" :key="index" :value="cat">
        {{ cat }}
      </option>
    </select>
    <select v-model="selectedDate">
      <option value="December 2017">December 2017</option>
      <option value="October 2017">October 2017</option>
    </select>
    <div class="row">
      <!-- <script
        async
        src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=5205487e-6336-410e-bc20-a17c2bd3408b&height=190px&width=320px&view=Tables"
        type="text/javascript"
      ></script> -->
      <!-- <script
        async
        src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=835aa132-662e-4343-9915-70a540efc797&height=190px&width=320px&view=Tables"
        type="text/javascript"
      ></script>
      <script
        async
        src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=084189cd-ce50-42b3-a65e-68b793d932fb&height=190px&width=320px&view=Tables"
        type="text/javascript"
      ></script> -->
      <!-- <script
        async
        src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=96f4ed76-f2a6-4db5-865d-93e36f56951c&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJqb3JkYW4ubG9yaG9AdG91Y2FudG9jby5jb20iLCJpYXQiOjE2MDk4NDMwMDMsImV4cCI6MTYxMjQzNTAwM30.Mn-jJcFUisQ9fDVaopspf96Gbwjl90_q1PQt20KyWRY&height=190px&width=320px&stage=staging&view=Tables&stage=staging"
        type="text/javascript"
      ></script> -->
    </div>
    <div class="row">
      <div class="story-container">
        <script
          async
          src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=25e3c3d2-589e-4229-9f9c-7ca034a3dc08&view=Tables"
          type="text/javascript"
        ></script>
      </div>
      <div class="story-container">
        <script
          async
          src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=c8126df7-b6a7-4f82-a391-8f6f7c027f12&view=Tables"
          type="text/javascript"
        ></script>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      categories: [
        'Tables',
        'Accessories',
        'Storage',
        'Fasteners',
        'Labels',
        'Art',
        'Appliances',
        'Bookcases',
        'Binders',
        'Supplies',
        'Paper',
        'Chairs',
        'Phones',
        'Envelopes',
        'Machines',
        'Furnishings',
        'Copiers',
      ],
      selectedView: 'Tables',
      selectedDate: 'December 2017',
      toucanSDK: null,
    }
  },
  watch: {
    selectedView(newVal, oldVal) {
      this.toucanSDK.setRequesterValueForAllEmbeds(
        'APP_REPORT_REQUESTER_ID',
        newVal
      )
    },
    selectedDate(newVal, oldVal) {
      this.toucanSDK.setRequesterValueForAllEmbeds(
        'APP_DATE_REQUESTER_ID',
        newVal
      )
    },
  },
  mounted() {
    this.toucanSDK = new window.TcTcEmbed()
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.row {
  display: flex;
  width: 100%;
}

.story-container {
  display: flex;
  height: 80vh;
  width: 100%;
}
</style>
