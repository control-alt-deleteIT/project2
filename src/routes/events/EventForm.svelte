<script lang="ts">
    export let onClose: () => void;
    export let existingEvents: { name: string; startDate: string; endDate: string; time: string }[] = [];
    let step = 1;

    let formData = {
        name: '',
        contactNumber: '',
        email: '',
        startDate: '',
        endDate: '',
        time: '',
        eventType: ''
    };

    let errors: { [key: string]: string } = {};

    function validateStep() {
        errors = {};
        if (step === 1) {
            if (!formData.name) errors.name = "Name is required.";
            if (!formData.contactNumber) errors.contactNumber = "Contact Number is required.";
        }
        if (step === 2) {
            if (!formData.startDate) errors.startDate = "Start Date is required.";
            if (!formData.endDate) errors.endDate = "End Date is required.";
            if (new Date(formData.startDate) > new Date(formData.endDate)) {
                errors.dateRange = "End date cannot be before the start date.";
            }
        }
        if (step === 3 && !formData.time) {
            errors.time = "Event time is required.";
        }

        if (step === 2 && checkForOverlap()) {
            errors.dateOverlap = "The event dates overlap with an existing event.";
        }

        return Object.keys(errors).length === 0;
    }

    function nextStep() {
        if (validateStep()) {
            step += 1;
        }
    }

    function previousStep() {
        if (step > 1) step -= 1;
    }

    function checkForOverlap() {
        const start = new Date(formData.startDate);
        const end = new Date(formData.endDate);
        return existingEvents.some(event => {
            const eventStart = new Date(event.startDate);
            const eventEnd = new Date(event.endDate);
            return (start < eventEnd && end > eventStart); 
        });
    }

    function submitForm() {
        if (validateStep()) {
            console.log('Form submitted:', formData);
            onClose();
            addEvent(formData);
        }
    }

    function addEvent(eventData: typeof formData) {
        existingEvents.push(eventData);
    }
</script>

<div
    class="fixed inset-0 bg-gray-800 bg-opacity-50 flex items-center justify-center"
    role="button"
    tabindex="0"
    aria-label="Close Modal"
    on:click={onClose}
    on:keydown={(event) => event.key === 'Enter' && onClose()}
></div>

<div class="bg-white rounded-lg p-8 shadow-lg relative z-10 w-full max-w-md">
    <h2 class="text-2xl font-semibold mb-4">Create Event</h2>

    {#if step === 1}
        <input type="text" class="border p-2 w-full rounded mb-2" placeholder="Name..." bind:value={formData.name} />
        {#if errors.name}<p class="text-red-500 text-sm">{errors.name}</p>{/if}

        <input type="text" class="border p-2 w-full rounded mb-2" placeholder="Contact Number..." bind:value={formData.contactNumber} />
        {#if errors.contactNumber}<p class="text-red-500 text-sm">{errors.contactNumber}</p>{/if}
    {/if}

    {#if step === 2}
        <input type="email" class="border p-2 w-full rounded mb-2" placeholder="Email..." bind:value={formData.email} />
        {#if errors.email}<p class="text-red-500 text-sm">{errors.email}</p>{/if}

        <div class="flex flex-col">
            <label for="startDate" class="text-sm font-semibold mb-1">Start Date</label>
            <input id="startDate" type="date" class="border p-2 rounded mb-2" bind:value={formData.startDate} />
            {#if errors.startDate}<p class="text-red-500 text-sm">{errors.startDate}</p>{/if}
        </div>
        <div class="flex flex-col">
            <label for="endDate" class="text-sm font-semibold mb-1">End Date</label>
            <input id="endDate" type="date" class="border p-2 rounded mb-2" bind:value={formData.endDate} />
            {#if errors.endDate}<p class="text-red-500 text-sm">{errors.endDate}</p>{/if}
            {#if errors.dateRange}<p class="text-red-500 text-sm">{errors.dateRange}</p>{/if}
            {#if errors.dateOverlap}<p class="text-red-500 text-sm">{errors.dateOverlap}</p>{/if}
        </div>
    {/if}

    {#if step === 3}
    <label for="time" class="text-sm font-semibold">Enter Time</label>
    <input id="time" type="time" class="border p-2 w-full rounded mb-2" bind:value={formData.time} />
    {#if errors.time}<p class="text-red-500 text-sm">{errors.time}</p>{/if}

        <select class="border p-2 w-full rounded mb-2" bind:value={formData.eventType}>
            <option disabled value="">Type of Event...</option>
            <!-- Event types can be added here -->
        </select>
    {/if}

    <div class="flex gap-2 mt-4">
        {#if step > 1}
            <button class="bg-gray-200 text-gray-700 px-4 py-2 rounded" on:click={previousStep}>Back</button>
        {/if}
        {#if step < 3}
            <button class="bg-pink-600 text-white px-4 py-2 rounded hover:bg-pink-700" on:click={nextStep}>Next</button>
        {:else}
            <button class="bg-pink-600 text-white px-4 py-2 rounded hover:bg-pink-700" on:click={submitForm}>Create Event</button>
        {/if}
        <button class="bg-gray-200 text-gray-700 px-4 py-2 rounded" on:click={onClose}>Cancel</button>
    </div>
</div>