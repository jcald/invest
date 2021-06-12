<script>
	let
		minSum = 50000,
		maxSum = 10000000,
		sum = minSum,
		minMonth = 4,
		maxMonth = 36,
		month = minMonth,
		yearPercent = 24;

	$: profit = sum * yearPercent * month * 30 / (30 * 12) / 100;
	$: everyMonthProfit = profit / month;
	
	const formatMoney = new Intl.NumberFormat('es-Es', {
		style: 'currency',
		currency: 'SOL',
		maximumFractionDigits: 2
	});
	const displayMoney = number => formatMoney.format(number);
</script>

<h4>Su monto de inversión: {displayMoney(sum)}</h4>
{displayMoney(minSum)} <input type="range" min="{minSum}" max="{maxSum}" bind:value="{sum}"> {displayMoney(maxSum)}
<h4>Plazo de inversión: {month} meses</h4>
{minMonth} mes. <input type="range" min="{minMonth}" max="{maxMonth}" bind:value="{month}"> {maxMonth} mes.

<h4>{yearPercent}% anual</h4>
<h3>Tus ganancias: {displayMoney(profit)}</h3>
<h2>Pagos mensuales: {displayMoney(everyMonthProfit)}</h2>
