<script setup>
import { reactive, ref, computed, onMounted } from "vue";

import { Line, Bar, Radar, PolarArea, Pie, Doughnut } from "vue-chartjs";

import { Chart, registerables } from "chart.js";

import {
  Dataset,
  DatasetItem,
  DatasetInfo,
  DatasetPager,
  DatasetSearch,
  DatasetShow,
} from "vue-dataset";

Chart.register(...registerables);

Chart.defaults.color = "#818d96";
Chart.defaults.font.weight = "600";
Chart.defaults.scale.grid.color = "rgba(0, 0, 0, .05)";
Chart.defaults.scale.grid.zeroLineColor = "rgba(0, 0, 0, .1)";
Chart.defaults.scale.beginAtZero = true;
Chart.defaults.elements.line.borderWidth = 2;
Chart.defaults.elements.point.radius = 4;
Chart.defaults.elements.point.hoverRadius = 6;
Chart.defaults.plugins.tooltip.radius = 3;
Chart.defaults.plugins.legend.labels.boxWidth = 15;

const dataset = {
  members: [
    {
      id: 1,
      nama: "John Doe",
      usia: 28,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 5000,
    },
    {
      id: 2,
      nama: "Jane Doe",
      usia: 25,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6000,
    },
    {
      id: 3,
      nama: "Alice Johnson",
      usia: 32,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 7500,
    },
    {
      id: 4,
      nama: "Bob Smith",
      usia: 40,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8000,
    },
    {
      id: 5,
      nama: "Eva Martinez",
      usia: 35,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6200,
    },
    {
      id: 6,
      nama: "David Brown",
      usia: 45,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8500,
    },
    {
      id: 7,
      nama: "Sara Miller",
      usia: 30,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 7000,
    },
    {
      id: 8,
      nama: "Michael Wilson",
      usia: 38,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7800,
    },
    {
      id: 9,
      nama: "Olivia Davis",
      usia: 29,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5500,
    },
    {
      id: 10,
      nama: "Daniel Garcia",
      usia: 33,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7200,
    },
    {
      id: 11,
      nama: "Ava Taylor",
      usia: 27,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6800,
    },
    {
      id: 12,
      nama: "Matthew Hernandez",
      usia: 36,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 9200,
    },
    {
      id: 13,
      nama: "Sophia Turner",
      usia: 31,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6700,
    },
    {
      id: 14,
      nama: "Jackson Miller",
      usia: 42,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8900,
    },
    {
      id: 15,
      nama: "Amelia Harris",
      usia: 26,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5800,
    },
    {
      id: 16,
      nama: "Henry Thompson",
      usia: 39,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7600,
    },
    {
      id: 17,
      nama: "Lily Davis",
      usia: 28,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5100,
    },
    {
      id: 18,
      nama: "Ethan Martinez",
      usia: 34,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 6800,
    },
    {
      id: 19,
      nama: "Isabella Wilson",
      usia: 29,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6200,
    },
    {
      id: 20,
      nama: "Mason Brown",
      usia: 37,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8100,
    },
    {
      id: 21,
      nama: "Chloe Taylor",
      usia: 24,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5400,
    },
    {
      id: 22,
      nama: "Liam Hernandez",
      usia: 33,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7400,
    },
    {
      id: 23,
      nama: "Grace Miller",
      usia: 30,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6900,
    },
    {
      id: 24,
      nama: "Alexander Garcia",
      usia: 41,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8800,
    },
    {
      id: 25,
      nama: "Scarlett Taylor",
      usia: 28,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6300,
    },
    {
      id: 26,
      nama: "Benjamin Davis",
      usia: 35,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8000,
    },
    {
      id: 27,
      nama: "Aria Martinez",
      usia: 27,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6700,
    },
    {
      id: 28,
      nama: "Lucas Wilson",
      usia: 39,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7500,
    },
    {
      id: 29,
      nama: "Zoe Brown",
      usia: 25,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5600,
    },
    {
      id: 30,
      nama: "Carter Taylor",
      usia: 36,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8300,
    },
    {
      id: 31,
      nama: "Mia Hernandez",
      usia: 32,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 7100,
    },
    {
      id: 32,
      nama: "Jayden Garcia",
      usia: 38,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8900,
    },
    {
      id: 33,
      nama: "Evelyn Wilson",
      usia: 29,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5900,
    },
    {
      id: 34,
      nama: "Gabriel Davis",
      usia: 40,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8200,
    },
    {
      id: 35,
      nama: "Madison Taylor",
      usia: 26,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6000,
    },
    {
      id: 36,
      nama: "Logan Hernandez",
      usia: 31,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7200,
    },
    {
      id: 37,
      nama: "Avery Brown",
      usia: 33,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6400,
    },
    {
      id: 38,
      nama: "Jackson Wilson",
      usia: 37,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8600,
    },
    {
      id: 39,
      nama: "Luna Garcia",
      usia: 28,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6100,
    },
    {
      id: 40,
      nama: "Caleb Taylor",
      usia: 34,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7700,
    },
    {
      id: 41,
      nama: "Hazel Hernandez",
      usia: 30,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6900,
    },
    {
      id: 42,
      nama: "Elijah Brown",
      usia: 39,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8400,
    },
    {
      id: 43,
      nama: "Stella Davis",
      usia: 27,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5700,
    },
    {
      id: 44,
      nama: "Grayson Taylor",
      usia: 35,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7900,
    },
    {
      id: 45,
      nama: "Nova Martinez",
      usia: 29,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6300,
    },
    {
      id: 46,
      nama: "Leo Wilson",
      usia: 41,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 9100,
    },
    {
      id: 47,
      nama: "Lily Taylor",
      usia: 28,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5800,
    },
    {
      id: 48,
      nama: "Sebastian Garcia",
      usia: 42,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8800,
    },
    {
      id: 49,
      nama: "Aria Hernandez",
      usia: 31,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 7000,
    },
    {
      id: 50,
      nama: "Ethan Brown",
      usia: 33,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7500,
    },
    {
      id: 51,
      nama: "Hannah Taylor",
      usia: 26,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6100,
    },
    {
      id: 52,
      nama: "Mason Wilson",
      usia: 36,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8300,
    },
    {
      id: 53,
      nama: "Aurora Davis",
      usia: 32,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 7200,
    },
    {
      id: 54,
      nama: "Oliver Martinez",
      usia: 38,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 8600,
    },
    {
      id: 55,
      nama: "Paisley Brown",
      usia: 27,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5500,
    },
    {
      id: 56,
      nama: "Liam Taylor",
      usia: 37,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7900,
    },
    {
      id: 57,
      nama: "Penelope Hernandez",
      usia: 28,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6000,
    },
    {
      id: 58,
      nama: "Lucas Davis",
      usia: 39,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 9000,
    },
    {
      id: 59,
      nama: "Scarlett Taylor",
      usia: 25,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 5400,
    },
    {
      id: 60,
      nama: "Elijah Garcia",
      usia: 34,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 7800,
    },
    {
      id: 61,
      nama: "Ava Wilson",
      usia: 30,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 6700,
    },
    {
      id: 62,
      nama: "Jackson Brown",
      usia: 41,
      jenis_kelamin: "Laki-laki",
      penghasilan_bulanan: 9200,
    },
    {
      id: 63,
      nama: "Chloe Taylor",
      usia: 29,
      jenis_kelamin: "Perempuan",
      penghasilan_bulanan: 9200,
    },
  ],
};

const jumlahPerempuan = dataset.members.filter(
  (member) => member.jenis_kelamin === "Perempuan"
).length;

const jumlahLakilaki = dataset.members.filter(
  (member) => member.jenis_kelamin === "Laki-laki"
).length;

const chartPolarPieDonutData = {
  datasets: [
    {
      data: [jumlahPerempuan, jumlahLakilaki],
      backgroundColor: [
        "rgba(255, 99, 132, 0.7)", // warna untuk perempuan
        "rgba(54, 162, 235, 0.7)", // warna untuk laki-laki
      ],
    },
  ],
  labels: ["Perempuan", "Laki-laki"],
};

const penghasilanBulanan = dataset.members.map(
  (member) => member.penghasilan_bulanan
);

const chartLinesBarsRadarData = {
  labels: ["5000-6000", "6001-7000", "7001-8000", "8001-9000"],
  datasets: [
    {
      label: "Penghasilan Bulanan Member",
      data: penghasilanBulanan,
      fill: true,
      backgroundColor: "rgba(171, 227, 125, .5)",
      borderColor: "rgba(171, 227, 125, 1)",
      pointBackgroundColor: "rgba(171, 227, 125, 1)",
      pointBorderColor: "#fff",
      pointHoverBackgroundColor: "#fff",
      pointHoverBorderColor: "rgba(171, 227, 125, 1)",
      data: [15, 16, 20, 25, 23, 25, 32],
    },
  ],
};

const tables = [
  {
    name: "Nama",
    field: "nama",
    sort: "",
  },
  {
    name: "Usia",
    field: "usia",
    sort: "",
  },
  {
    name: "Jenis Kelamin",
    field: "jenis_kelamin",
    sort: "",
  },
  {
    name: "Penghasilan Bulanan",
    field: "penghasilan_bulanan",
    sort: "",
  },
];

const sortBy = computed(() => {
  return tables.reduce((acc, o) => {
    if (o.sort) {
      o.sort === "asc" ? acc.push(o.field) : acc.push("-" + o.field);
    }
    return acc;
  }, []);
});

// On sort th click
function onSort(event, i) {
  let toset;
  const sortEl = tables[i];

  if (!event.shiftKey) {
    tables.forEach((o) => {
      if (o.field !== sortEl.field) {
        o.sort = "";
      }
    });
  }

  if (!sortEl.sort) {
    toset = "asc";
  }

  if (sortEl.sort === "desc") {
    toset = event.shiftKey ? "" : "asc";
  }

  if (sortEl.sort === "asc") {
    toset = "desc";
  }

  sortEl.sort = toset;
}

// Apply a few Bootstrap 5 optimizations
onMounted(() => {
  // Remove labels from
  document.querySelectorAll("#datasetLength label").forEach((el) => {
    el.remove();
  });

  // Replace select classes
  let selectLength = document.querySelector("#datasetLength select");

  selectLength.classList = "";
  selectLength.classList.add("form-select");
  selectLength.style.width = "80px";
});

const users = ref(dataset.members);
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
      <div class="col-sm-6 col-xl-2">
        <div class="dropdown">
          <button
            type="button"
            class="btn btn-light dropdown-toggle"
            id="dropdown-jk"
            data-bs-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            Jenis Kelamin
          </button>
          <div
            class="dropdown-menu fs-sm dropdown-fixed-width"
            aria-labelledby="dropdown-jk"
          >
            <a class="dropdown-item" href="javascript:void(0)">Perempuan</a>
            <a class="dropdown-item" href="javascript:void(0)">Laki-laki</a>
          </div>
        </div>
      </div>
      <div class="col-sm-6 col-xl-2">
        <div class="dropdown">
          <button
            type="button"
            class="btn btn-light dropdown-toggle"
            id="dropdown-usia"
            data-bs-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            Usia
          </button>
          <div
            class="dropdown-menu fs-sm dropdown-fixed-width"
            aria-labelledby="dropdown-usia"
          >
            <a class="dropdown-item" href="javascript:void(0)"
              >Remaja (12-24)</a
            >
            <a class="dropdown-item" href="javascript:void(0)"
              >Dewasa (25-40)</a
            >
            <a class="dropdown-item" href="javascript:void(0)"
              >Orang Tua (41-70)</a
            >
          </div>
        </div>
      </div>
      <div class="col-sm-6 col-xl-4">
        <div class="dropdown">
          <button
            type="button"
            class="btn btn-light dropdown-toggle"
            id="dropdown-penghasilan"
            data-bs-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            Penghasilan Bulanan
          </button>
          <div
            class="dropdown-menu fs-sm dropdown-fixed-width"
            aria-labelledby="dropdown-penghasilan"
          >
            <a class="dropdown-item" href="javascript:void(0)">5000-6000</a>
            <a class="dropdown-item" href="javascript:void(0)">6001-7000</a>
            <a class="dropdown-item" href="javascript:void(0)">7001-8000</a>
            <a class="dropdown-item" href="javascript:void(0)">8001-9000</a>
          </div>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-xl-6">
        <!-- Pie Chart -->
        <BaseBlock title="Pie" content-full content-class="text-center">
          <div class="py-3 px-xxl-7">
            <Pie
              :data="chartPolarPieDonutData"
              :options="{ maintainAspectRatio: false }"
              style="height: 350px"
            />
          </div>
        </BaseBlock>
        <!-- END Pie Chart -->
      </div>
      <div class="col-xl-6">
        <!-- Bars Chart -->
        <BaseBlock title="Bars" content-full content-class="text-center">
          <div class="py-3">
            <Bar
              :data="chartLinesBarsRadarData"
              :options="{ maintainAspectRatio: false }"
              style="height: 350px"
            />
          </div>
        </BaseBlock>
        <!-- END Bars Chart -->
      </div>
    </div>

    <BaseBlock title="Daftar Member" content-full>
      <Dataset
        v-slot="{ ds }"
        :ds-data="users"
        :ds-sortby="sortBy"
        :ds-search-in="[
          'id',
          'nama',
          'usia',
          'jenis_kelamin',
          'penghasilan_bulanan',
        ]"
      >
        <div class="row" :data-page-count="ds.dsPagecount">
          <div id="datasetLength" class="col-md-8 py-2">
            <DatasetShow />
          </div>
          <div class="col-md-4 py-2">
            <DatasetSearch ds-search-placeholder="Search..." />
          </div>
        </div>
        <hr />
        <div class="row">
          <div class="col-md-12">
            <div class="table-responsive">
              <table class="table table-striped mb-0">
                <thead>
                  <tr>
                    <th scope="table">No</th>
                    <th
                      v-for="(th, index) in tables"
                      :key="th.field"
                      :class="['sort', th.sort]"
                      @click="onSort($event, index)"
                    >
                      {{ th.nama }} <i class="gg-select float-end"></i>
                    </th>
                  </tr>
                </thead>
                <DatasetItem tag="tbody" class="fs-sm">
                  <template #default="{ row, rowIndex }">
                    <tr>
                      <th scope="row">{{ rowIndex + 1 }}</th>
                      <td style="min-width: 150px">{{ row.nama }}</td>
                      <td>{{ row.usia }}</td>
                      <td style="min-width: 150px">
                        {{ row.jenis_kelamin }}
                      </td>
                      <td style="min-width: 150px">
                        {{ row.penghasilan_bulanan }}
                      </td>
                    </tr>
                  </template>
                </DatasetItem>
              </table>
            </div>
          </div>
        </div>
        <div
          class="d-flex flex-md-row flex-column justify-content-between align-items-center"
        >
          <DatasetInfo class="py-3 fs-sm" />
          <DatasetPager class="flex-wrap py-3 fs-sm" />
        </div>
      </Dataset>
    </BaseBlock>
  </div>
</template>

<style lang="scss" scoped>
.gg-select {
  box-sizing: border-box;
  position: relative;
  display: block;
  transform: scale(1);
  width: 22px;
  height: 22px;
}
.gg-select::after,
.gg-select::before {
  content: "";
  display: block;
  box-sizing: border-box;
  position: absolute;
  width: 8px;
  height: 8px;
  left: 7px;
  transform: rotate(-45deg);
}
.gg-select::before {
  border-left: 2px solid;
  border-bottom: 2px solid;
  bottom: 4px;
  opacity: 0.3;
}
.gg-select::after {
  border-right: 2px solid;
  border-top: 2px solid;
  top: 4px;
  opacity: 0.3;
}
th.sort {
  cursor: pointer;
  user-select: none;
  &.asc {
    .gg-select::after {
      opacity: 1;
    }
  }
  &.desc {
    .gg-select::before {
      opacity: 1;
    }
  }
}

.dropdown-fixed-width {
  width: 200px; // You can adjust the width as needed
}
</style>
