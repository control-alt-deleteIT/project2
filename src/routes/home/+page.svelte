<script>
  import Homenav from './homenav.svelte';

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

<Homenav />

<div class="p-4">
  <h2 class="text-3xl font-semibold">Dashboard</h2>
  <h1 class="text-2xl mt-2 mb-4">Current Events</h1>
  
  <div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
    {#each currentEvents as event}
      <div class="p-4 bg-white rounded-lg shadow-md">
        <h4 class="text-xl font-semibold">{event.name}</h4>
        <p><strong>Start Date:</strong> {event.startDate}</p>
        <p><strong>End Date:</strong> {event.endDate}</p>
        <p><strong>Time:</strong> {event.time}</p>
      </div>
    {/each}
  </div>
</div>