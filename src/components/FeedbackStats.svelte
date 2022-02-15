<script>
    import { FeedbackStore } from '../stores'

    $: count = $FeedbackStore.length
    $: average = Math.floor(
        $FeedbackStore.reduce((a, { rating }) => a + rating, 0) /
            $FeedbackStore.length
    )
</script>

<div class="feedback-stats">
    <h4>{count} Reviews</h4>
    <h4>Ratings average {average ? average : '0'}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>
