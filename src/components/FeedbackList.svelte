<script>
    // import { onMount, onDestroy } from 'svelte'
    import { FeedbackStore } from '../stores'
    import { scale, fade } from 'svelte/transition'
    import FeedbackItem from './FeedbackItem.svelte'

    // slow way
    // let feedback = []

    // const unsubscribe = FeedbackStore.subscribe((data) => (feedback = data))

    // onDestroy(() => {
    //     unsubscribe()
    // })
</script>

<!-- EZ life -->
{#each $FeedbackStore as fb (fb.id)}
    <div out:fade={{ duration: 200 }} in:scale>
        <FeedbackItem item={fb} on:delete-feedback />
    </div>
{/each}
