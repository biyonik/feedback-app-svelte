<script>
    import Card from "./Card.svelte";
    import {FeedbackStore} from "../stores/stores";
    export let feedback;

    const handleDelete = itemId => {
        FeedbackStore.update((currentFeedback) => {
            return currentFeedback.filter(item => item.id != itemId);
        })
    }
</script>

<Card>
    <div class="num-display">
        {feedback.rating}
    </div>
    <button class="close" on:click={() => handleDelete(feedback.id)}>X</button>
    <p class="text-display">
        {feedback.text}
    </p>
</Card>

<style>
    .num-display {
        position: absolute;
        top: -1.875rem;
        left: -.875rem;
        width: 6rem;
        height: 6rem;
        background-color: #ff6a95;
        color: #fff;
        border: 1px #eee solid;
        border-radius: 50%;
        padding: .875rem;
        text-align: center;
        font-size: 2.2rem;
    }

    .close {
        position: absolute;
        top: .875rem;
        right: 1.75rem;
        cursor: pointer;
        background: none;
        border: none;
    }
</style>
