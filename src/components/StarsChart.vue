<script>
import { Bar } from "vue-chartjs";
import axios from "axios";

export default {
  extends: Bar,
  data() {
    return {
      vue_stars: {},
      angular_stats: {},
      ember_stats: {},
      svelte_stats: {},
      react_stats: {},
      chartData: {
        labels: ["Vue", "Angular", "Ember", "Svelte", "React"],
        datasets: [
          {
            // label: "Bar Chart",
            borderWidth: 1,
            backgroundColor: [
              "rgba(255, 99, 132, 0.2)",
              "rgba(54, 162, 235, 0.2)",
              "rgba(255, 206, 86, 0.2)",
              "rgba(75, 192, 192, 0.2)",
              "rgba(153, 102, 255, 0.2)",
            ],
            borderColor: [
              "rgba(255,99,132,1)",
              "rgba(54, 162, 235, 1)",
              "rgba(255, 206, 86, 1)",
              "rgba(75, 192, 192, 1)",
              "rgba(153, 102, 255, 1)",
            ],
            pointBorderColor: "#2554FF",
            data: [],
          },
        ],
      },
      options: {
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
              },
              gridLines: {
                display: true,
              },
            },
          ],
          xAxes: [
            {
              gridLines: {
                display: false,
              },
            },
          ],
        },
        legend: {
          display: false,
        },
        responsive: true,
        maintainAspectRatio: false,
      },
    };
  },
  created: function () {
    this.vueStats();
    this.angularStats();
    this.emberStats();
    this.svelteStats();
    this.reactStats();
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  },
  methods: {
    vueStats: function () {
      axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
        console.log(response.data);
        this.vue_stats = response.data;
      });
    },
    angularStats: function () {
      axios.get("https://api.github.com/repos/angular/angular.js").then((response) => {
        console.log(response.data);
        this.angular_stats = response.data;
      });
    },
    emberStats: function () {
      axios.get("https://api.github.com/repos/emberjs/ember.js").then((response) => {
        console.log(response.data);
        this.ember_stats = response.data;
      });
    },
    svelteStats: function () {
      axios.get("https://api.github.com/repos/sveltejs/svelte").then((response) => {
        console.log(response.data);
        this.svelte_stats = response.data;
      });
    },
    reactStats: function () {
      axios.get("https://api.github.com/repos/facebook/react").then((response) => {
        console.log(response.data);
        this.react_stats = response.data;
      });
    },
  },
};
</script>
