<template>
    <div class="col-12" v-if="!getDetailStudent">
        <Bar
            :chart-data="chartData"
            class="col-10 m-auto"
            style="width: 400px; height: 400px"
        />
        <h6 class="fw-bolder col-12 text-center mt-3">
            Biểu đồ thể hiện số lượng sinh viên tại các đơn vị thực tập
        </h6>
    </div>
</template>

<script>
import { Bar } from "vue-chartjs";
import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    BarElement,
    CategoryScale,
    LinearScale,
} from "chart.js";
import { mapGetters } from "vuex";

ChartJS.register(
    Title,
    Tooltip,
    Legend,
    BarElement,
    CategoryScale,
    LinearScale
);

export default {
    name: "BarChart",
    components: { Bar },
    computed: {
        chartData() {
            return {
                labels: [
                    "TMA",
                    "UNIT",
                    "NFQ Asia",
                    "BE solution",
                    "Khác",
                ],
                datasets: [
                    {
                        label: "Số lượng sinh viên",
                        backgroundColor: "#1f5caa",
                        data: [40, 20, 12, 10, 3],
                    },
                ],
            };
        },
        ...mapGetters({
            getDetailStudent: "getDetailStudent",
        }),
    },
};
</script>
