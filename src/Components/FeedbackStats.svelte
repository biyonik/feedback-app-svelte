<script>
    import {FeedbackStore} from "../stores/stores";

    export let count = 0;
    export let averageRating = 0;

    $: count = $FeedbackStore.length;
    $: averageRating = count > 0 ? $FeedbackStore.reduce((prevValue, {rating}) => {
        return prevValue + rating
    }, 0) / count : 0;
</script>

<div class="feedback-stats">
    <h4>Feedback count is: {count}</h4>
    <h4>Average rating is: {averageRating}</h4>
</div>


<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>
