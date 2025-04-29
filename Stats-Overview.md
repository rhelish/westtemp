
# Flash Rates


```dataviewjs
const rawData = await dv.query('TABLE file.name, pflash, bflash, yflash, rflash WHERE contains(file.name, "WEST") SORT file.name LIMIT 5');

const rows = rawData.value.values;

const labels = rows.map(x => x[1]);
const data = [rows.map(x => x[2]), rows.map(x => x[3]), rows.map(x => x[4]),rows.map(x => x[5])];
const colorMap = ["#800080", "#0000ff", "#Ffff00", "#880808"]

const chartData = {  
    type: 'bar',
    data: {
        labels: labels,
		datasets: [
		{label: "Purple Flashes", data: data[0], backgroundColor: colorMap[0], borderColor: colorMap[0], borderWidth: 1},
		{label: "Blue Flashes", data: data[1], backgroundColor: colorMap[1], borderColor: colorMap[1], borderWidth: 1},
		{label: "Yellow Flashes", data: data[2], backgroundColor: colorMap[2], borderColor: colorMap[2], borderWidth: 1},
		{label: "Red Flashes", data: data[3], backgroundColor: colorMap[3], borderColor: colorMap[3], borderWidth: 1}
		]
    }
}

window.renderChart(chartData, this.container);
```

# Unfinished V Multi V Flash

```dataviewjs
const rawData = await dv.query('TABLE file.name, rflash, rmulti, rdnf, bflash, pmulti, pdnf WHERE contains(file.name, "WEST") SORT file.name LIMIT 5');

const rows = rawData.value.values;

const labels = rows.map(x => x[1]);
const data = [rows.map(x => x[2]), rows.map(x => x[3]), rows.map(x => x[4]),rows.map(x => x[5])];
//where [1] = flash rates, [2] = flash+multi, and [3] = flash+multi+dnf
const colorMap = ["#800080", "#0000ff", "#Ffff00", "#880808"]

const chartData = {  
    type: 'bar',
    data: {
        labels: labels,
		datasets: [
		{label: "Red, Flash", data: data[0], backgroundColor: colorMap[3], borderColor: colorMap[3], borderWidth: 3},
		{label: "Red, Multi", data: data[1], backgroundColor: "#88080880", borderColor: colorMap[3], borderWidth: 3},
		{label: "Red, DNF", data: data[2], backgroundColor: "#ffffff11", borderColor: colorMap[3], borderWidth: 3}
		]
    },
    options: {
	    scales: {
		    x: {
			    stacked: true
			},
			y: {
				stacked: true
			}
		}
	}
}

window.renderChart(chartData, this.container);
```

