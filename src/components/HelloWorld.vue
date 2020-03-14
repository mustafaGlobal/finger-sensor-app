<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Serial
        </h1>
        <v-btn @click="connectSerial">Connect</v-btn>
        <apexchart
          width="500"
          type="bar"
          :options="chartOptions"
          :series="series"
        ></apexchart>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",
  methods: {
    connectSerial() {
      let SerialPort = require("serialport");
      let port = new SerialPort("/dev/ttyUSB1", {
        baudRate: 115200
      });

      port.write("I'm alive\n");
    }
  },
  data: () => ({
    chartOptions: {
      chart: {
        id: "vuechart-example"
      },
      xaxis: {
        categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998]
      },
      theme: {
        mode: "dark",
        palette: "palette4"
      }
    },
    series: [
      {
        name: "series-1",
        data: [30, 40, 45, 50, 49, 60, 70, 91]
      }
    ]
  })
};
</script>

<style scoped></style>
l
