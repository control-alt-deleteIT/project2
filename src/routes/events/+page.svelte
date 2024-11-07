<script>
    import './events.css';
    import EventForm from './EventForm.svelte';

    let showEventForm = false;
    let events = [
        { name: 'Sportfest', startDate: '2023-09-21', endDate: '2023-09-24', time: '09:00' },
        { name: 'Birthday', startDate: '2023-09-15', endDate: '2023-09-15', time: '18:00' },
        { name: 'Exam', startDate: '2023-10-15', endDate: '2023-10-19', time: '10:00' },
        { name: 'Concert', startDate: '2023-11-01', endDate: '2023-11-01', time: '20:00' },
        { name: 'Conference', startDate: '2023-11-05', endDate: '2023-11-06', time: '08:00' },
        { name: 'Workshop', startDate: '2023-11-10', endDate: '2023-11-12', time: '09:30' }
    ];

    function toggleEventForm() {
        showEventForm = !showEventForm;
    }
</script>

<div class="events-page-wrapper">
    <div class="events-container">
        <input type="text" placeholder="Search..." class="search-bar" />
        <button class="create-event" on:click={toggleEventForm}>Create Event +</button>
    </div>

    <div class="event-cards">
        {#each events as event}
            <div class="event-card">
                <h3>{event.name}</h3>
                <p>{event.startDate} - {event.endDate}</p>
                <p>{event.time}</p>
            </div>
        {/each}
    </div>
</div>

{#if showEventForm}
    <EventForm onClose={toggleEventForm} existingEvents={events} />
{/if}
