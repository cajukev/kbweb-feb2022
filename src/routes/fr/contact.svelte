<script>
  import Contact from '/src/components/pages/contact.svelte';
  import {lang, page} from '../../stores'
	import {onMount} from 'svelte'
  let timeslots;

	onMount(async () => {
		const res = await fetch('/api/timeslots')
			.then((response) => response.json())
			.then((json) => {
				return json;
			});

		timeslots = await res;
	})

	let timeslots_prop= {}
	$: timeslots_prop = timeslots
  $lang = "fr"
  $page = "contact"
  
</script>
  
<Contact lang={"fr"} timeslots={timeslots_prop}></Contact>