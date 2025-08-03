<script lang="ts">
	interface Props {
		title: string;
		description: string;
	}

	let { title, description = 'Default value' }: Props = $props();
</script>

<p><b>{title}</b><br />{description}</p>
