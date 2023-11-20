<!-- Developed by Taipei Urban Intelligence Center 2023 -->

<script setup>
import { ref } from "vue";

const props = defineProps(["chart_config", "activeChart", "series"]);

const chartOptions = ref({
	chart: {
		toolbar: {
			show: false,
			tools: {
				zoom: true,
			},
		},
		stacked: false,
		type: "line",
	},
	colors: props.chart_config.color,
	dataLabels: {
		enabled: false,
	},
	grid: {
		show: false,
	},
	markers: {
		hover: {
			size: 12,
		},
		size: 3,
		strokeWidth: 0,
	},
	stroke: {
		width: [1, 1],
	},
	xaxis: {
		type: "datetime",
	},
	yaxis: [
		{
			tooltip: {
				enabled: false,
			},
			axisTicks: {
				show: true,
			},
			axisBorder: {
				show: true,
			},
		},
		{
			opposite: true,
			tooltip: {
				enabled: false,
			},
			axisTicks: {
				show: true,
			},
			axisBorder: {
				show: true,
			},
			labels: {},
			title: {},
		},
	],
	tooltip: {
		fixed: {
			enabled: false,
			position: "topRight", // topRight, topLeft, bottomRight, bottomLeft
			offsetY: 0,
			offsetX: 0,
		},
		style: {
			fontSize: "12px",
		},
		fillSeriesColor: false,
		theme: "dark",
		followCursor: true,
	},
	legend: {
		horizontalAlign: "left",
		offsetX: 40,
		show: props.series.length > 1 ? true : false,
	},
});
</script>

<template>
	<div id="chartContainer" v-if="activeChart === 'MultipleYAxisChart'">
		<apexchart
			width="100%"
			height="350px"
			type="line"
			:options="chartOptions"
			:series="series"
		></apexchart>
	</div>
</template>
s
