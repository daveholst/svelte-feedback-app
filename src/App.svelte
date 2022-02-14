<script>
    import FeedbackList from './components/FeedbackList.svelte'
    import FeedbackStats from './components/FeedbackStats.svelte'
    import FeedbackForm from './components/FeedbackForm.svelte'
    let feedback = [
        {
            id: 1,
            rating: 10,
            text: 'Irure ut ipsum amet labore ullamco minim consectetur ipsum do. Labore voluptate ea esse ipsum voluptate anim qui labore esse irure adipisicing. Velit veniam culpa cupidatat et. Commodo cupidatat sint id non ea sunt nulla consectetur sunt aute. Dolor consectetur irure ullamco quis qui labore sunt sunt duis. Nisi excepteur voluptate labore fugiat labore consequat eu. Veniam commodo aliquip est commodo voluptate do ad laborum excepteur.',
        },
        {
            id: 2,
            rating: 9,
            text: 'Irure ut ipsum amet labore ullamco minim consectetur ipsum do. Labore voluptate ea esse ipsum voluptate anim qui labore esse irure adipisicing. Velit veniam culpa cupidatat et. Commodo cupidatat sint id non ea sunt nulla consectetur sunt aute. Dolor consectetur irure ullamco quis qui labore sunt sunt duis. Nisi excepteur voluptate labore fugiat labore consequat eu. Veniam commodo aliquip est commodo voluptate do ad laborum excepteur.',
        },
        {
            id: 3,
            rating: 6,
            text: 'Irure ut ipsum amet labore ullamco minim consectetur ipsum do. Labore voluptate ea esse ipsum voluptate anim qui labore esse irure adipisicing. Velit veniam culpa cupidatat et. Commodo cupidatat sint id non ea sunt nulla consectetur sunt aute. Dolor consectetur irure ullamco quis qui labore sunt sunt duis. Nisi excepteur voluptate labore fugiat labore consequat eu. Veniam commodo aliquip est commodo voluptate do ad laborum excepteur.',
        },
    ]
    $: count = feedback.length
    $: average = Math.floor(
        feedback.reduce((a, { rating }) => a + rating, 0) / feedback.length
    )

    function deleteFeedback(event) {
        const itemId = event.detail
        feedback = feedback.filter((item) => item.id !== itemId)
    }
    function addFeedback(event) {
        const feedbackItem = event.detail
        feedback = [...feedback, feedbackItem]
    }
</script>

<main class="container">
    <FeedbackForm on:add-feedback={addFeedback} />
    <FeedbackStats {count} {average} />
    <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>

<style>
    header {
        max-width: 400px;
        margin: auto;
    }
    header h2 {
        font-size: 22px;
        font-weight: 600;
        text-align: center;
    }
    .input-group {
        display: flex;
        flex-direction: row;
        border: 1px solid #ccc;
        padding: 8px 10px;
        border-radius: 8px;
        margin-top: 15px;
    }
    input {
        flex-grow: 2;
        border: none;
        font-size: 16px;
    }
    input:focus {
        outline: none;
    }
    .message {
        padding-top: 10px;
        text-align: center;
        color: rebeccapurple;
    }
</style>
