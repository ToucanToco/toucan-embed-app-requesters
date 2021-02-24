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
      <button class="switch" @click="switchTo">
        Switch to {{ switchLabel }}
      </button>
    </div>
    <div class="row comment-container">
      Theses filters aren't element that came from Toucan Toco. They're binded
      to configured app requesters.
    </div>
    <div v-if="!isDashboardBuilderDisplayed" class="multiple-stories">
      <div class="row tiles-container">
        <div class="tile-container">
          <script
            async
            src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=5205487e-6336-410e-bc20-a17c2bd3408b&view=Tables"
            type="text/javascript"
          ></script>
        </div>
        <div class="tile-container">
          <script
            async
            src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=835aa132-662e-4343-9915-70a540efc797&view=Tables"
            type="text/javascript"
          ></script>
        </div>
        <div class="tile-container">
          <script
            async
            src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=084189cd-ce50-42b3-a65e-68b793d932fb&view=Tables"
            type="text/javascript"
          ></script>
        </div>
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
    <div v-else>
      <script
        async
        src="https://demo-embed.toucantoco.com/scripts/embedLauncher.js?id=2c5162ae-1a71-4124-b988-137bba5d9f73"
        type="text/javascript"
      ></script>
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
      isDashboardBuilderDisplayed: false,
    }
  },
  computed: {
    switchLabel() {
      return this.isDashboardBuilderDisplayed
        ? 'in-house dashboard'
        : 'Dashboard Builder'
    },
  },
  watch: {
    selectedView(newVal) {
      this.toucanSDK.setRequesterValueForAllEmbeds(
        'APP_REPORT_REQUESTER_ID',
        newVal
      )
    },
    selectedDate(newVal) {
      this.toucanSDK.setRequesterValueForAllEmbeds(
        'APP_DATE_REQUESTER_ID',
        newVal
      )
    },
  },
  mounted() {
    this.toucanSDK = new window.TcTcEmbed()
  },
  methods: {
    switchTo() {
      // Switch
      this.isDashboardBuilderDisplayed = !this.isDashboardBuilderDisplayed

      // Reset view
      this.selectedView = 'Tables'

      // Update date
      this.selectedDate = 'December 2017'
    },
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

.tiles-container {
  justify-content: space-around;
  margin-bottom: 40px;
}

.story-container {
  display: flex;
  height: 65vh;
  width: 49%;
  border: 1px solid #cecece;
  border-radius: 2px;
  -webkit-box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.08);
  box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.08);
}

.tile-container {
  width: 440px;
  height: 240px;
  border: 1px solid #cecece;
  border-radius: 2px;
  -webkit-box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.08);
  box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.08);
}

.filters-container {
  display: flex;
  border: 1px solid #cecece;
  height: 60px;
}

.comment-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60px;
  background-color: #f5f5f5;
  border: 1px solid #cecece;
  font-weight: bold;
  color: rgb(64, 64, 64);
  text-align: center;
  font-size: 18px;
  margin-bottom: 20px;
}

.filter-group {
  display: flex;
  flex-direction: column;
  color: #888;
  padding: 10px;
}

.filter-group__label {
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

.switch {
  margin-left: auto;
  margin-top: auto;
  margin-bottom: auto;
  margin-right: 35px;
  display: flex;
  height: 45px;
  border-radius: 4px;
  padding: 0 10px;
  justify-content: center;
  align-items: center;
  border: 1px solid #2665a3;
  color: white;
  background-color: #2665a3;
  transition: all 0.3s ease-in;
  cursor: pointer;
  outline: none;
}

.switch:hover {
  color: #2665a3;
  background-color: white;
}
</style>
