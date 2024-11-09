<script>
  import Eventsnav from './eventsnav.svelte';
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

<Eventsnav />

<div class="p-4">
  <div class="flex justify-between items-center mb-4">
      <input type="text" placeholder="Search..." class="px-4 py-2 rounded-md border border-gray-300" />
      <button class="bg-pink-600 text-white px-4 py-2 rounded-lg hover:bg-pink-700" on:click={toggleEventForm}>
          Create Event +
      </button>
  </div>

  <div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
      {#each events as event}
          <div class="p-4 bg-white rounded-lg shadow-md">
              <h3 class="text-xl font-semibold">{event.name}</h3>
              <p>{event.startDate} - {event.endDate}</p>
              <p>{event.time}</p>
          </div>
      {/each}
  </div>

  {#if showEventForm}
      <div class="fixed inset-0 bg-gray-800 bg-opacity-50 flex items-center justify-center">
          <EventForm onClose={toggleEventForm} existingEvents={events} />
      </div>
  {/if}
</div>
