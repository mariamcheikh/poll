<template>
  <div id="chartdiv"></div>
</template>
<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";
import am4themes_kelly from "@amcharts/amcharts4/themes/kelly";
am4core.useTheme(am4themes_animated);
am4core.useTheme(am4themes_kelly);

export default {
  name: "PollCharts",

  data() {
    return {
      chart: null,
      chartData: [],
    };
  },
  props: ["question", "answers", "vote"],
  methods: {
    chartInit() {
      // Create chart instance
      var chart = am4core.create("chartdiv", am4charts.XYChart);
      chart.marginRight = 400;
      chart.data = [
        {
          vote: "Answers",
        },
      ];
      // Create axes
      var categoryAxis = chart.xAxes.push(new am4charts.CategoryAxis());
      categoryAxis.dataFields.category = "vote";
      chart.yAxes.push(new am4charts.ValueAxis());
      // Create series
      var series = chart.series.push(new am4charts.ColumnSeries());
      series.dataFields.valueY = "Answers";
      series.dataFields.categoryX = "vote";
      // Add cursor
      chart.cursor = new am4charts.XYCursor();

      this.chart = chart;
    },
    updatePollChart(votes) {
      var data = [];
      for (const [key, value] of Object.entries(votes)) {
        data.push({ vote: key, Answers: value });
      }

      this.chart.data = data;
    },
  },
  mounted() {
    this.chartInit();
  },
};
</script>

<style scoped>
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica,
    Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  font-size: 9pt;
}

#chartdiv {
  width: 100%;
  height: 400px;
}
</style>
