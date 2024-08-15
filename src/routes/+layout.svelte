<script>
	import '../app.css';
</script>

<body class="min-h-full bg-gradient-to-br from-sky-600 to-indigo-400">
	<nav class="flex gap-24 justify-center border-b-2 max-w-lg m-auto border-slate-800">
		<a class="p-4" href="/">Home</a>
		<a class="p-4" href="/about">About</a>
	</nav>

	<slot />
</body>
