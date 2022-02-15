<script>
    import Card from './Card.svelte'
    import { FeedbackStore } from '../stores'
    export let item

    function handleDelete(itemId) {
        FeedbackStore.update((currentFeedback) => {
            return currentFeedback.filter((item) => item.id !== itemId)
        })
    }
</script>

<Card>
    <div class="num-display">{item.rating}</div>
    <button class="close" on:click={() => handleDelete(item.id)}>❌</button>
    <p class="text-display">{item.text}</p>
</Card>

<style>
    .num-display {
        position: absolute;
        top: -10px;
        left: -10px;
        width: 50px;
        height: 50px;
        background: #ff6a95;
        color: #fff;
        border: 1px #eee solid;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 19px;
    }
    .close {
        position: absolute;
        top: 20px;
        right: 20px;
        font-size: 18px;
        cursor: pointer;
        background: none;
        border: none;
    }
</style>
