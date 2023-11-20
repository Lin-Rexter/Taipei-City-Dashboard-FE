<!-- Developed by Taipei Urban Intelligence Center 2023 -->

<script setup>
import { ref } from "vue";

const props = defineProps(["chart_config", "activeChart", "series"]);

const chartOptions = ref({
	chart: {
		stacked: true,
		toolbar: {
			show: false,
		},
	},
	colors: props.chart_config.color,
	grid: {
		show: false,
	},
	legend: {
		show: props.chart_config.categories ? true : false,
	},
	markers: {
		hover: {
			sizeOffset: 5,
		},
	},
	stroke: {
		curve: "straight",
	},
});
</script>

<template>
	<div v-if="activeChart === 'RangeAreaChart'">
		<apexchart
			width="100%"
			height="350px"
			type="rangeArea"
			:options="chartOptions"
			:series="series"
		></apexchart>
	</div>
</template>
