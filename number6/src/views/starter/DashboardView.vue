<script setup>
import { reactive, ref } from "vue";
import { Line, Bar } from "vue-chartjs";
import { Chart, registerables } from "chart.js";

Chart.register(...registerables);

// Set Global Chart.js configuration
Chart.defaults.color = "#818d96";
Chart.defaults.scale.grid.lineWidth = 0;
Chart.defaults.scale.beginAtZero = true;
Chart.defaults.datasets.bar.maxBarThickness = 45;
Chart.defaults.elements.bar.borderRadius = 4;
Chart.defaults.elements.bar.borderSkipped = false;
Chart.defaults.elements.point.radius = 0;
Chart.defaults.elements.point.hoverRadius = 0;
Chart.defaults.plugins.tooltip.radius = 3;
Chart.defaults.plugins.legend.labels.boxWidth = 10;

const orderSearch = ref(false);

// Chart Earnings data
const earningsData = reactive({
  labels: ["MON", "TUE", "WED", "THU", "FRI", "SAT", "SUN"],
  datasets: [
    {
      label: "This Week",
      fill: true,
      backgroundColor: "rgba(100, 116, 139, .7)",
      borderColor: "transparent",
      pointBackgroundColor: "rgba(100, 116, 139, 1)",
      pointBorderColor: "#fff",
      pointHoverBackgroundColor: "#fff",
      pointHoverBorderColor: "rgba(100, 116, 139, 1)",
      data: [716, 628, 1056, 560, 956, 890, 790],
    },
    {
      label: "Last Week",
      fill: true,
      backgroundColor: "rgba(100, 116, 139, .15)",
      borderColor: "transparent",
      pointBackgroundColor: "rgba(100, 116, 139, 1)",
      pointBorderColor: "#fff",
      pointHoverBackgroundColor: "#fff",
      pointHoverBorderColor: "rgba(100, 116, 139, 1)",
      data: [1160, 923, 1052, 1300, 880, 926, 963],
    },
  ],
});

// Chart Earnings options
const earningsOptions = reactive({
  responsive: true,
  maintainAspectRatio: false,
  scales: {
    x: {
      display: false,
      grid: {
        drawBorder: false,
      },
    },
    y: {
      display: false,
      grid: {
        drawBorder: false,
      },
    },
  },
  interaction: {
    intersect: false,
  },
  plugins: {
    legend: {
      labels: {
        boxHeight: 10,
        font: {
          size: 14,
        },
      },
    },
    tooltip: {
      callbacks: {
        label: function (context) {
          return context.dataset.label + ": $" + context.parsed.y;
        },
      },
    },
  },
});

// Chart Total Orders data
const totalOrdersData = reactive({
  labels: [
    "MON",
    "TUE",
    "WED",
    "THU",
    "FRI",
    "SAT",
    "SUN",
    "MON",
    "TUE",
    "WED",
    "THU",
    "FRI",
    "SAT",
    "SUN",
  ],
  datasets: [
    {
      label: "Total Orders",
      fill: true,
      backgroundColor: "rgba(220, 38, 38, .15)",
      borderColor: "transparent",
      pointBackgroundColor: "rgba(220, 38, 38, 1)",
      pointBorderColor: "#fff",
      pointHoverBackgroundColor: "#fff",
      pointHoverBorderColor: "rgba(220, 38, 38, 1)",
      data: [33, 29, 32, 37, 38, 30, 34, 28, 43, 45, 26, 45, 49, 39],
    },
  ],
});

// Chart Total Orders options
const totalOrdersOptions = reactive({
  maintainAspectRatio: false,
  tension: 0.4,
  scales: {
    x: {
      display: false,
    },
    y: {
      display: false,
    },
  },
  interaction: {
    intersect: false,
  },
  plugins: {
    legend: {
      display: false,
    },
    tooltip: {
      callbacks: {
        label: function (context) {
          return " " + context.parsed.y + " Orders";
        },
      },
    },
  },
});

// Chart Total Earnings data
const totalEarningsData = reactive({
  labels: [
    "MON",
    "TUE",
    "WED",
    "THU",
    "FRI",
    "SAT",
    "SUN",
    "MON",
    "TUE",
    "WED",
    "THU",
    "FRI",
    "SAT",
    "SUN",
  ],
  datasets: [
    {
      label: "Total Earnings",
      fill: true,
      backgroundColor: "rgba(101, 163, 13, .15)",
      borderColor: "transparent",
      pointBackgroundColor: "rgba(101, 163, 13, 1)",
      pointBorderColor: "#fff",
      pointHoverBackgroundColor: "#fff",
      pointHoverBorderColor: "rgba(101, 163, 13, 1)",
      data: [
        716, 1185, 750, 1365, 956, 890, 1200, 968, 1158, 1025, 920, 1190, 720,
        1352,
      ],
    },
  ],
});

// Chart Total Earnings options
const totalEarningsOptions = reactive({
  maintainAspectRatio: false,
  tension: 0.4,
  scales: {
    x: {
      display: false,
    },
    y: {
      display: false,
    },
  },
  interaction: {
    intersect: false,
  },
  plugins: {
    legend: {
      display: false,
    },
    tooltip: {
      callbacks: {
        label: function (context) {
          return " $" + context.parsed.y;
        },
      },
    },
  },
});

// Chart New Customers data
const newCustomersData = reactive({
  labels: [
    "MON",
    "TUE",
    "WED",
    "THU",
    "FRI",
    "SAT",
    "SUN",
    "MON",
    "TUE",
    "WED",
    "THU",
    "FRI",
    "SAT",
    "SUN",
  ],
  datasets: [
    {
      label: "Total Orders",
      fill: true,
      backgroundColor: "rgba(101, 163, 13, .15)",
      borderColor: "transparent",
      pointBackgroundColor: "rgba(101, 163, 13, 1)",
      pointBorderColor: "#fff",
      pointHoverBackgroundColor: "#fff",
      pointHoverBorderColor: "rgba(101, 163, 13, 1)",
      data: [25, 15, 36, 14, 29, 19, 36, 41, 28, 26, 29, 33, 23, 41],
    },
  ],
});

// Chart New Customers options
const newCustomersOptions = reactive({
  maintainAspectRatio: false,
  tension: 0.4,
  scales: {
    x: {
      display: false,
    },
    y: {
      display: false,
    },
  },
  interaction: {
    intersect: false,
  },
  plugins: {
    legend: {
      display: false,
    },
    tooltip: {
      callbacks: {
        label: function (context) {
          return " " + context.parsed.y + " Customers";
        },
      },
    },
  },
});
</script>

<template>
  <BasePageHeading title="Laporan">
    <template #extra>
      <button type="button" class="btn btn-alt-primary" v-click-ripple>
        <i class="fa fa-download opacity-50 me-1"></i>
        Download
      </button>
    </template>
  </BasePageHeading>

  <div class="content">
    <div class="row items-push">
      <div class="col-12 col-sm-6 col-xl-2 mb-3">
        <div class="block-content flex-grow-1 d-flex justify-content-between">
          <dl class="mb-0">
            <dt class="fs-3 fw-bold">570</dt>
            <dd class="fs-sm fw-medium text-muted mb-0">Total Orders</dd>
          </dl>
          <div>
            <div
              class="d-inline-block px-2 py-1 rounded-3 fs-xs fw-semibold text-danger bg-danger-light"
            >
              <i class="fa fa-caret-down me-1"></i>
              2.2%
            </div>
          </div>
        </div>
        <!-- <BaseBlock class="small-square-block">
          <div class="inner-content">
            <p class="block-title">Member Aktif</p>
            <p class="member-count">27<span class="total-count">/134</span></p>
          </div>
        </BaseBlock> -->
      </div>
      <div class="col-sm-6 col-xl-2">
        <BaseBlock class="small-square-block">
          <div class="inner-content">
            <p class="block-title">Laki-laki</p>
            <p class="member-count">37%</p>
          </div>
        </BaseBlock>
      </div>
      <div class="col-sm-6 col-xl-8">
        <BaseBlock class="small-square-block">
          <div class="inner-content">
            <p class="block-title">Perempuan</p>
            <p class="member-count">67%</p>
          </div>
        </BaseBlock>
      </div>

      <div class="col-12 col-sm-6 col-xl-2 mb-3">
        <BaseBlock class="small-square-block">
          <div class="inner-content">
            <p class="block-title">Remaja</p>
            <p class="member-count">25%</p>
          </div>
        </BaseBlock>
      </div>
      <div class="col-sm-6 col-xl-2">
        <BaseBlock class="small-square-block">
          <div class="inner-content">
            <p class="block-title">Dewasa (24-35)</p>
            <p class="member-count">45%</p>
          </div>
        </BaseBlock>
      </div>
      <div class="col-sm-6 col-xl-4">
        <BaseBlock class="small-square-block">
          <div class="inner-content">
            <p class="block-title">Orang Tua (>35)</p>
            <p class="member-count">67%</p>
          </div>
        </BaseBlock>
      </div>

      <div class="col-12 col-md-6 col-xl-4 mb-3">
        <BaseBlock class="rectangle-block">
          <div class="inner-content">
            <p class="block-title">Rata-rata Penghasilan Member</p>
            <!-- <p class="info-text">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            </p> -->
          </div>
        </BaseBlock>
      </div>
    </div>
  </div>

  <!-- <div class="content">
    <div class="row items-push">
      <div class="col-sm-6 col-xl-4">
        <BaseBlock title="Block" class="h-100 mb-0">
          <p>
            This is a backend layout based page which you can use as a base for
            your backend pages.
          </p>
          <p>
            We created a custom Backend layout variation (
            <code>layouts/variations/BackendStarter.vue</code>) to showcase how
            easily you can add extra layout variations and override the default
            content of the partial elements.
          </p>
        </BaseBlock>
      </div>
      <div class="col-sm-6 col-xl-4">
        <BaseBlock title="Block" class="h-100 mb-0">
          <p>...</p>
        </BaseBlock>
      </div>
      <div class="col-xl-4">
        <BaseBlock title="Block" class="h-100 mb-0">
          <p>...</p>
        </BaseBlock>
      </div>
    </div>
  </div> -->
</template>

<style scoped>
.small-square-block {
  width: 200px;
  height: 200px;
  margin-top: 10px;
  margin-right: 15px;
  margin-bottom: 15px;
  position: relative;
  text-align: left;
}
.small-square-block:last-child {
  margin-right: 0;
}

.small-square-block .inner-content {
  position: absolute;
  top: 20px;
  left: 0;
  right: 0;
  /* transform: translate(-50%, -50%);
  width: 100%; */
  text-align: left;
}
.small-square-block .block-title {
  /* position: absolute;
  top: 10px;
  left: 0;
  right: 0; */
  /* font-weight: bold; */
  font-size: 18px;
  /* margin-top: 5px; */
  text-align: left;
  margin-left: 20px;
  /* transform: translate(-50%, -50%);
  width: 100%;
  text-align: center; */
}

.small-square-block .member-count {
  font-weight: bold;
  font-size: 18px;
  margin-left: 20px;
}

.small-square-block .total-count {
  font-weight: normal;
}

.rectangle-block {
  width: 1000px;
  height: 400px;
  margin-top: 10px;
  margin-bottom: 15px;
  position: relative;
  text-align: left;
}

.rectangle-block .inner-content {
  position: absolute;
  top: 20px;
  left: 0;
  right: 0;
  text-align: left;
}

.rectangle-block .block-title {
  font-size: 18px;
  text-align: left;
  margin-left: 20px;
}

.rectangle-block .info-text {
  font-size: 16px;
  margin-left: 20px;
}
</style>
