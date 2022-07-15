<script>
    import {FeedbackStore} from "../stores/stores";
    import {fade, scale} from 'svelte/transition';
    import FeedbackItem from "./FeedbackItem.svelte";
    import {onDestroy, onMount} from "svelte";

    // let feedbacks = [];
    //
    // const unsubscribe = FeedbackStore.subscribe((data) => {
    //     feedbacks = data;
    // })
    //
    // onMount(() => {
    //
    // })
    //
    // onDestroy(() => {
    //     unsubscribe();
    // })
</script>

<div>
    <h2>Feedback List</h2>
    {#if $FeedbackStore.length === 0}
        <h2>Hiç bir feedback verisi bulunamadı!</h2>
    {:else}
        {#each $FeedbackStore as feedback (feedback.id)}
            <div in:scale out:fade="{{duration: 500}}">
                <FeedbackItem feedback={feedback}/>
            </div>
        {/each}
    {/if}
</div>

<style>

</style>
