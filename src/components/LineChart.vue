<template>
  <div>
    <h2>Line Chart</h2>
    <div ref="lineChart" style="width: 100%; height: 400px;"></div>
  </div>
</template>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";

am4core.useTheme(am4themes_animated);

export default {
  name: "LineChart",
  data() {
    return {
      chartData: [
        { date: new Date(2023, 0, 1), value: 10 },
        { date: new Date(2023, 1, 1), value: 15 },
        { date: new Date(2023, 2, 1), value: 8 },
        // Add more data points as needed
      ],
      chart: null,
    };
  },
  mounted() {
    this.chart = am4core.create(this.$refs.lineChart, am4charts.XYChart);

    this.chart.data = this.chartData;

    // Create the date axis
    let dateAxis = this.chart.xAxes.push(new am4charts.DateAxis());
    dateAxis.title.text = "Date";

    // Create the value axis
    let valueAxis = this.chart.yAxes.push(new am4charts.ValueAxis());
    valueAxis.title.text = "Value";

    // Create the line series
    let series = this.chart.series.push(new am4charts.LineSeries());
    series.dataFields.dateX = "date";
    series.dataFields.valueY = "value";
    series.tooltipText = "{valueY.value}";
  },
  beforeUnmount() {
    if (this.chart) {
      this.chart.dispose();
    }
  },
};
</script>
