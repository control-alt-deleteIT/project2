<script lang="ts">
  import Eventsnav from './eventsnav.svelte';
  import EventForm from './EventForm.svelte';

  // Define the Event type
  type Event = {
    name: string;
    startDate: string;
    endDate: string;
    time: string;
    description: string;
  };

  let showEventForm = false;
  let showDeleteModal = false;
  let eventToDelete: Event | null = null; // Explicitly define the type of eventToDelete
  let searchQuery = '';
  let events: Event[] = [ // Apply Event type to the events array
    { name: 'Sportfest', startDate: '2023-09-21', endDate: '2023-09-24', time: '09:00', description: 'A fun-filled event with various sports competitions and activities for everyone to participate in.' },
    { name: 'Birthday', startDate: '2023-09-15', endDate: '2023-09-15', time: '18:00', description: 'Celebrating a special birthday with close friends and family.' },
    { name: 'Exam', startDate: '2023-10-15', endDate: '2023-10-19', time: '10:00', description: 'A week of exams across different subjects for students.' },
    { name: 'Concert', startDate: '2023-11-01', endDate: '2023-11-01', time: '20:00', description: 'A live music concert featuring local bands and artists.' },
    { name: 'Conference', startDate: '2023-11-05', endDate: '2023-11-06', time: '08:00', description: 'An academic conference where experts from various fields share their research and insights.' },
    { name: 'Workshop', startDate: '2023-11-10', endDate: '2023-11-12', time: '09:30', description: 'A hands-on workshop designed to enhance skills in a particular field.' },
    { name: 'Web Development Bootcamp', startDate: '2023-12-01', endDate: '2023-12-07', time: '10:00', description: 'A week-long intensive course on web development covering HTML, CSS, and JavaScript.' },
    { name: 'Marketing Workshop', startDate: '2023-12-03', endDate: '2023-12-03', time: '14:00', description: 'A workshop focusing on modern marketing strategies and tools.' },
    { name: 'Networking Event', startDate: '2023-12-05', endDate: '2023-12-05', time: '18:00', description: 'An event for professionals to meet, mingle, and expand their network.' },
    { name: 'Coding Challenge', startDate: '2023-12-07', endDate: '2023-12-07', time: '08:00', description: 'A coding competition where developers compete to solve problems in the shortest time.' },
    { name: 'Science Conference', startDate: '2023-12-09', endDate: '2023-12-11', time: '09:00', description: 'A gathering of scientists and researchers discussing recent advances in various scientific fields.' },
    { name: 'Christmas Party', startDate: '2023-12-15', endDate: '2023-12-15', time: '19:00', description: 'A festive party celebrating the holiday season with music, food, and cheer.' },
    { name: 'Tech Talk', startDate: '2023-12-17', endDate: '2023-12-17', time: '11:00', description: 'A presentation on the latest trends and innovations in technology.' },
    { name: 'New Year Countdown', startDate: '2023-12-31', endDate: '2023-12-31', time: '23:00', description: 'A lively event to celebrate the arrival of the New Year with fireworks and festivities.' }
  ];

  function toggleEventForm() {
    showEventForm = !showEventForm;
  }

  // Function to filter events based on search query
  $: filteredEvents = events.filter(event =>
    event.name.toLowerCase().includes(searchQuery.toLowerCase())
  ).sort((a, b) => a.name.localeCompare(b.name)); // Sort events alphabetically

  function deleteEvent() {
    if (eventToDelete) {
      events = events.filter(event => event !== eventToDelete);
      showDeleteModal = false; // Hide the modal after deletion
    }
  }
</script>

<Eventsnav />

<div class="p-6 mt-12">
    <h1 class="text-4xl font-bold mb-8 mt-7 text-left text-[#66FCF1]">Your Events</h1>
  <!-- Search Bar and Button Section -->
  <div class="flex justify-between items-center mb-6 mt-11">
    <input 
      type="text" 
      placeholder="Search events..." 
      class="px-4 py-3 rounded-md border bg-transparent border-[#C5C6C7] text-[#1F2833] focus:outline-none focus:ring-2 focus:ring-[#66FCF1] transition-all duration-300 w-3/4"
      bind:value={searchQuery} 
    />
    <button class="bg-[#66FCF1] text-[#1F2833] px-6 py-3 rounded-lg hover:bg-[#45A29E] transition-all duration-300 font-semibold" on:click={toggleEventForm}>
      Add Event +
    </button>
  </div>
  
  <!-- Event Cards Grid -->
  <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
    {#each filteredEvents as event}
      <div class="p-6 bg-[#1F2833] text-[#C5C6C7] rounded-lg shadow-lg hover:shadow-xl transition-all duration-300">
        <!-- Event Title -->
        <h3 class="text-2xl font-semibold text-[#66FCF1]">{event.name}</h3>
        
        <!-- Event Description -->
        <p class="text-sm text-[#C5C6C7] mt-2">{event.description}</p>

        <!-- Event Dates -->
        <p class="mt-2">{event.startDate}</p>
        <p class="mt-1 text-[#C5C6C7]">Start Time: {event.time}</p>
        <p class="mt-1 text-[#C5C6C7]">End Date: {event.endDate}</p>
  
        <!-- Delete Button -->
        <button class="mt-4 text-[#f7941d] font-semibold hover:text-[#C5C6C7] transition-all duration-300" on:click={() => { eventToDelete = event; showDeleteModal = true; }}>
          Delete
        </button>
      </div>
    {/each}
  </div>
  
  <!-- Event Form Modal -->
  {#if showEventForm}
    <div class="fixed inset-0 bg-[#0B0C10] bg-opacity-70 flex items-center justify-center z-20">
      <EventForm onClose={toggleEventForm} existingEvents={events} />
    </div>
  {/if}

  {#if showDeleteModal}
  <div class="fixed inset-0 bg-gray-800 bg-opacity-50 flex items-center justify-center z-20">
    <div class="bg-white rounded-lg p-8 shadow-lg relative z-10 w-full max-w-md">
      <h2 class="text-2xl font-semibold mb-4">Confirm Deletion</h2>
      <p class="mb-4">Are you sure you want to delete the event "{eventToDelete?.name}"?</p>

      <div class="flex gap-2 mt-4">
        <button class="bg-[#f7941d] text-white px-4 py-2 rounded" on:click={() => { 
          events = events.filter(event => event !== eventToDelete); 
          showDeleteModal = false; // Hide the modal after deletion
          eventToDelete = null; // Clear selected event
        }}>
          Yes, Delete
        </button>
        <button class="bg-gray-200 text-gray-700 px-4 py-2 rounded" on:click={() => { showDeleteModal = false; eventToDelete = null; }}>
          Cancel
        </button>
      </div>
    </div>
  </div>
{/if}
</div>
