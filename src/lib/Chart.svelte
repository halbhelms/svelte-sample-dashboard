<script>
  import { arc, max, scaleBand, scaleOrdinal, scaleRadial, stack } from "d3";
  import data from "./radialStacked-data.js"; // or pass data to component as prop
  import SectionHeading from './SectionHeading.svelte'
  
  const width = 1000; // width of inner radius inverted, in pixels
  const innerRadius = 180; // radius of inner circle, in pixels
  const colorRange = ['#98abc5','#8a89a6','#7b6888','#6b486b','#a05d56','#d0743c','#ff8c00']; // fill colors for each bar stack - MUST match number of datasets
  const chartScale = 0.4; // scale factor from the center
  const sorted = true; // whether to sort the data by descending total
  const varFontSize = 10; // font size of chart text, in pixels
  const tickColor = '#000'; // color of inner radius ticks
  const ringColor = '#000'; // color of scale rings
  const scaleColor = '#000'; // color of scale text
  const scaleStroke = '#fff'; // color of scale text background/stroke
  const rectLength = 18; // width of  color legend key, in pixels
  const height = width;
  const outerRadius = width * chartScale;
  const keys = Object.keys(data[0]).slice(0, -1);
  const groupId = keys[0];
  $: reactiveData = sorted === true
    ? [...data].sort((a, b) => b.total - a.total)
    : [...data];

  $: reactiveXScale = scaleBand()
    .domain(reactiveData.map((d) => d[groupId]))
    .range([0, 2 * Math.PI])
    .align(0);

  const yScale = scaleRadial()
    .domain([0, max(data, (d) => d.total)])
    .range([innerRadius, outerRadius]);

  const zScale = scaleOrdinal().domain(keys.slice(1)).range(colorRange);

  const d3arc = arc()
    .innerRadius((d) => yScale(d[0]))
    .outerRadius((d) => yScale(d[1]))
    .startAngle((d) => reactiveXScale(d.data[groupId]))
    .endAngle((d) => reactiveXScale(d.data[groupId]) + reactiveXScale.bandwidth())
    .padAngle(0.01)
    .padRadius(innerRadius);
</script>

<div class="my-chart">
  <div class="heading">
    <SectionHeading title="Cool Chart" subTitle="Svend3r"/>
  </div>
<svg
  class="radial-chart"
  viewBox="{-width / 2} {-height / 2} {width} {height}"
  font-size="{varFontSize}px"
>
  <g class="chart-render">
    {#each stack().keys(keys.slice(1))(reactiveData) as cData}
      <g fill={zScale(cData.key)}>
        {#each cData as d}
          <path d={d3arc(d)} />
        {/each}
      </g>
    {/each}
  </g>
  <g class="x-axis" text-anchor="middle">
    {#each reactiveData as d}
      <g
        transform="
        rotate({((reactiveXScale(d[groupId]) + reactiveXScale.bandwidth() / 2) * 180) / Math.PI - 90})
        translate({innerRadius},0)
      "
      >
        <line x2="-5" stroke={tickColor} />
        <text
          transform={(reactiveXScale(d[groupId]) + reactiveXScale.bandwidth() / 2 + Math.PI / 2) %
            (2 * Math.PI) <
          Math.PI
            ? "rotate(90) translate(0,16)"
            : "rotate(-90) translate(0,-9)"}>{d[groupId]}</text
        >
      </g>
    {/each}
  </g>
  <g class="y-axis" text-anchor="end">
    <text x="-6" y={-yScale(yScale.ticks(10).pop())} dy="-1em">Population</text>
    {#each yScale.ticks(10).slice(1) as ydata}
      <g fill="none">
        <circle stroke={ringColor} stroke-opacity="0.5" r={yScale(ydata)} />
        <text
          x="-6"
          y={-yScale(ydata)}
          dy="0.35em"
          stroke={scaleStroke}
          stroke-width="5"
          fill={scaleColor}>{ydata}</text
        >
        <text
          x="-6"
          y={-yScale(ydata)}
          dy="0.35em"
          stroke="none"
          stroke-width="5"
          fill={scaleColor}>{ydata}</text
        >
      </g>
    {/each}
  </g>
  <g class="legend">
    {#each keys.slice(1).reverse() as lData, i}
      <g transform="translate(-40,{(i - (keys.length - 1) / 2) * 20})">
        <rect width={rectLength} height="18" fill={zScale(lData)} />
        <text x="24" y="9" dy="0.35em">{lData}</text>
      </g>
    {/each}
  </g>
</svg>
</div>

<style>
  .my-chart {
    background-color: white;
  }

  .heading {
    margin: 2rem 0 0 2rem;
    padding-top: 2rem;
  }
</style>