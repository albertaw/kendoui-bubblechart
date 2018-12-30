<template>
  <div id="app">
    <kendo-datasource
      ref="dataSource"
      :transport-read-url="'https://api.iextrading.com/1.0/stock/market/collection/tag?collectionName=Computer+Hardware'"
      :transport-read-data-type="'json'">
    </kendo-datasource>
    <kendo-chart
      :data-source-ref="'dataSource'"
      :title="title"
      :tooltip="tooltip"
      :series="series"
      :x-axis="xAxis"
      :y-axis="yAxis"
      >
    </kendo-chart>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: {
        text: 'Price vs Volume'
      },
      tooltip: {
        visible: true,
        template: '<strong>#: category #</strong> Volume: #: value.x # <br> Price: $#: value.y #'
      },
     series: [{
      type: 'bubble',
      xField: 'latestVolume',
      yField: 'close',
      sizeField: 'marketCap',
      categoryField: 'symbol'
     }],
     xAxis: {
      title: {
        text: 'Latest Volume'
      }
     },
     yAxis: {
      title: {
        text: 'Closing Price'
      }
     }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
