<script>
	let currentTime = $state(new Date());

	$effect(() => {
		const interval = setInterval(() => {
			currentTime = new Date();
		}, 1000);

		return () => clearInterval(interval);
	});

	let formattedDate = $derived(
		currentTime.toLocaleDateString('nl-NL', {
			weekday: 'long',
			year: 'numeric',
			month: 'long',
			day: 'numeric'
		})
	);

	let formattedTime = $derived(
		currentTime.toLocaleTimeString('nl-NL', {
			hour: '2-digit',
			minute: '2-digit',
			second: '2-digit'
		})
	);
</script>

<img src="/logo.png" alt="Logo" />
<p class="font-mono text-gray-100">{formattedDate} - {formattedTime}</p>
