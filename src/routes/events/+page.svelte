<script>
    import './events.css';
    import EventForm from './EventForm.svelte';
    
    let showEventForm = false;

    function toggleEventForm() {
        showEventForm = !showEventForm;
    }
</script>

<div class="events-container">
    <input type="text" placeholder="Search..." class="search-bar" />
    <button class="create-event" on:click={toggleEventForm}>Create Event +</button>
</div>

<div class="event-cards">
    <div class="event-card pink">
        <h3>Sportfest</h3>
        <p>Sept. 21 - 24</p>
        <p>Mon-Thurs</p>
    </div>
    <div class="event-card cream">
        <h3>Birthday</h3>
        <p>Sept. 15</p>
        <p>Saturday</p>
    </div>
    <div class="event-card pink">
        <h3>Validation</h3>
        <p>Nov. 4</p>
        <p>Monday</p>
    </div>
    <div class="event-card cream">
        <h3>Birthday</h3>
        <p>Nov. 4</p>
        <p>Monday</p>
    </div>
    <div class="event-card pink">
        <h3>Exam</h3>
        <p>Oct. 15 - 19</p>
        <p>Tues-Sun</p>
    </div>
    <div class="event-card cream">
        <h3>Project Deadline</h3>
        <p>Nov. 4</p>
        <p>11:59PM</p>
    </div>
</div>

{#if showEventForm}
    <EventForm onClose={toggleEventForm} />
{/if}