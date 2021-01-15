<template>
  <div class="container">
    <div class="row filters-container">
      <div class="filter-group">
        <span class="filter-group__label">REPORT</span>
        <select v-model="selectedView">
          <option v-for="cat in categories" :key="cat" :value="cat">
            {{ cat }}
          </option>
        </select>
      </div>
      <div class="filter-group">
        <span class="filter-group__label">DATE</span>
        <select v-model="selectedDate">
          <option v-for="date in dates" :key="date" :value="date">
            {{ date }}
          </option>
        </select>
      </div>
    </div>
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
    <div class="row stories-container">
      <div class="story-container">
        <script
          async
          src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=25e3c3d2-589e-4229-9f9c-7ca034a3dc08&view=Tables&title=true"
          type="text/javascript"
        ></script>
      </div>
      <div class="story-container">
        <script
          async
          src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=c8126df7-b6a7-4f82-a391-8f6f7c027f12&view=Tables&title=true"
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
      dates: [
        'December 2017',
        'November 2017',
        'October 2017',
        'September 2017',
        'August 2017',
        'July 2017',
        'June 2017',
        'May 2017',
        'April 2017',
        'March 2017',
        'February 2017',
        'January 2017',
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
  padding: 20px;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.row {
  display: flex;
  width: 100%;
}

.stories-container {
  justify-content: space-between;
}

.story-container {
  display: flex;
  height: 80vh;
  width: 49%;
  border: 1px solid #cecece;
  border-radius: 2px;
  -webkit-box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.08);
  box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.08);
}

.filters-container {
  display: flex;
  border: 1px solid #cecece;
  margin-bottom: 20px;
  height: 60px;
}

.filter-group {
  display: flex;
  flex-direction: column;
  color: #888;
  padding: 10px;
}

.filter-group__label {
  /* display: flex;
  justify-content: start; */
  font-size: 11px;
  margin-left: 5px;
}

.filter-group select {
  border: none;
  font-weight: bold;
  color: #888;
  outline: 0;
  margin-top: 5px;
  font-size: 18px;
}
</style>
