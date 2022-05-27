<template>
  <div>
    <v-card class="mx-4">
      <div class="text-overline m-4">Users - La Mas Exitosa</div>
    </v-card>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2">
      <v-card class="flex m-4">
        <Apexcharts :options="options0" :series="series0" :type="type" />
      </v-card>
      <v-card class="flex m-4">
        <Apexcharts :options="options1" :series="series1" type="bar" />
      </v-card>
      <v-card class="flex m-4">
        <Apexcharts :options="options2" :series="series2" type="area" />
      </v-card>
      <v-card class="flex m-4">
        <Apexcharts :options="options3" :series="series3" type="boxPlot" />
      </v-card>
      <v-card class="flex m-4">
        <Apexcharts :options="options4" :series="series4" type="pie" />
      </v-card>
      <v-card class="flex m-4">
        <Apexcharts :options="options5" :series="series5" type="line"/>
      </v-card>
    </div>
  </div>
</template>

<script>
import Apexcharts from "../../components/common/apexcharts.vue";
export default {
  layout: "auth",
  components: { Apexcharts },

  data: () => ({
    type: "line",
    series0: [
      {
        name: "Sales",
        data: [12, 22, 45, 57, 82, 34, 46, 98, 23, 83, 94, 100]
      }
    ],
    options0: {
      xaxis: {
        categories: [
          "Jan",
          "Feb",
          "Mar",
          "Apr",
          "May",
          "Jun",
          "Jul",
          "Aug",
          "Sep",
          "Oct",
          "Nov",
          "Dec"
        ]
      },
      title: {
        text: "Chart 1",
        align: "left"
      },
      dataLabels: {
        enabled: false
      },
      colors: ['#6115A4'],
    },
    series1: [
      {
        name: "Sales",
        data: [52, 32, 32, 56, 78, 22, 40, 75, 65, 160, 67, 179]
      }
    ],
    options1: {
      xaxis: {
        categories: [
          "Jan",
          "Feb",
          "Mar",
          "Apr",
          "May",
          "Jun",
          "Jul",
          "Aug",
          "Sep",
          "Oct",
          "Nov",
          "Dec"
        ]
      },
      title: {
        text: "Chart 2",
        align: "left"
      },
      dataLabels: {
        enabled: false
      },
      colors: ['#6115A4'],
    },
    series2: [
      {
        name: "Sales",
        data: [77, 73, 85, 90, 56, 36, 64, 69, 71, 35, 21, 43]
      }
    ],
    options2: {
      xaxis: {
        categories: [
          "Jan",
          "Feb",
          "Mar",
          "Apr",
          "May",
          "Jun",
          "Jul",
          "Aug",
          "Sep",
          "Oct",
          "Nov",
          "Dec"
        ]
      },
      title: {
        text: "Chart 3",
        align: "left"
      },
      dataLabels: {
        enabled: false
      },
      colors: ['#6115A4'],
    },
    series3: [
      {
        data: [
          {
            x: "Category A",
            y: [54, 66, 69, 75, 88]
          },
          {
            x: "Category B",
            y: [43, 65, 69, 76, 81]
          },
          {
            x: "Category C",
            y: [31, 39, 45, 51, 59]
          },
          {
            x: "Category D",
            y: [39, 46, 55, 65, 71]
          },
          {
            x: "Category E",
            y: [29, 31, 35, 39, 44]
          },
          {
            x: "Category F",
            y: [41, 49, 58, 61, 67]
          },
          {
            x: "Category G",
            y: [54, 59, 66, 71, 88]
          }
        ]
      }
    ],
    options3: {
      chart: {
        type: "boxPlot",
        height: 350
      },
      title: {
        text: "Horizontal BoxPlot Chart",
        align: "left"
      },
      plotOptions: {
        bar: {
          horizontal: true,
          barHeight: "50%"
        },
        boxPlot: {
          colors: {
            upper: "#D960AB",
            lower: "#6115A4"
          }
        }
      },
      stroke: {
        colors: ["#3A3A3A"]
      },
      colors: ['#6115A4'],

    },
    series4: [25, 15, 44, 55, 41, 17],
    options4: {
      chart: {
        width: "100%",
        type: "pie"
      },
      labels: [
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ],
      theme: {
        monochrome: {
          enabled: true,
          color: '#D960AB'
        }
      },
      plotOptions: {
        pie: {
          dataLabels: {
            offset: -5
          }
        }
      },
      title: {
        text: "Monochrome Pie"
      },
      dataLabels: {
        formatter(val, opts) {
          const name = opts.w.globals.labels[opts.seriesIndex];
          return [name, val.toFixed(1) + "%"];
        }
      },
      legend: {
        show: false
      }
    },
    series5: [
      {
        name: "TEAM A",
        type: "column",
        data: [23, 11, 22, 27, 13, 22, 37, 21, 44, 22, 30]
      },
      {
        name: "TEAM B",
        type: "area",
        data: [44, 55, 41, 67, 22, 43, 21, 41, 56, 27, 43]
      },
      {
        name: "TEAM C",
        type: "line",
        data: [30, 25, 36, 30, 45, 35, 64, 52, 59, 36, 39]
      }
    ],
    options5: {
      chart: {
        height: 350,
        type: "line",
        stacked: false
      },
      stroke: {
        width: [0, 2, 5],
        curve: "smooth"
      },
      colors: ['#6115A4', '#D960AB', '#3a3a3a'],

      plotOptions: {
        bar: {
          columnWidth: "50%"
        }
      },

      fill: {
        opacity: [0.85, 0.25, 1],
        gradient: {
          inverseColors: false,
          shade: "light",
          type: "vertical",
          opacityFrom: 0.85,
          opacityTo: 0.55,
          stops: [0, 100, 100, 100]
        }
      },
      labels: [
        "01/01/2003",
        "02/01/2003",
        "03/01/2003",
        "04/01/2003",
        "05/01/2003",
        "06/01/2003",
        "07/01/2003",
        "08/01/2003",
        "09/01/2003",
        "10/01/2003",
        "11/01/2003"
      ],
      markers: {
        size: 0
      },
      xaxis: {
        type: "datetime"
      },
      yaxis: {
        title: {
          text: "Points"
        },
        min: 0
      },
      tooltip: {
        shared: true,
        intersect: false,
        y: {
          formatter: function(y) {
            if (typeof y !== "undefined") {
              return y.toFixed(0) + " points";
            }
            return y;
          }
        }
      }
    }
  })
};
</script>
<style>
</style>