<script>
    import './home.css';
    let currentEvents = [
        {
            name: "Annual Charity Gala",
            startDate: "2024-11-15",
            endDate: "2024-11-16",
            time: "6:00 PM",
        },
        {
            name: "Tech Conference 2024",
            startDate: "2024-12-01",
            endDate: "2024-12-02",
            time: "9:00 AM",
        },
        {
            name: "Art Exhibition",
            startDate: "2024-11-22",
            endDate: "2024-11-23",
            time: "5:00 PM",
        }
    ];
</script>

<div class="home-container">
    <h2 class="title">Dashboard</h2>
    <h1 class="tagline">Current Events</h1>
    
    <div class="current-events">
        <div class="event-cards">
            {#each currentEvents as event}
                <div class="event-card">
                    <h4>{event.name}</h4>
                    <p><strong>Start Date:</strong> {event.startDate}</p>
                    <p><strong>End Date:</strong> {event.endDate}</p>
                    <p><strong>Time:</strong> {event.time}</p>
                </div>
            {/each}
        </div>
    </div>
</div>