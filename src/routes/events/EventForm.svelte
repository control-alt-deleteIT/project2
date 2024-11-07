<script lang="ts">
    import './events.css';

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

<div class="modal-backdrop" on:click={onClose} on:keydown={(event) => event.key === 'Enter' && onClose()} role="button" tabindex="0" aria-label="Close event form"></div>

<div class="modal">
    <h2>Create Event</h2>

    {#if step === 1}
        <input type="text" class="input-field" placeholder="Name..." bind:value={formData.name} />
        {#if errors.name}<p class="error">{errors.name}</p>{/if}

        <input type="text" class="input-field" placeholder="Contact Number..." bind:value={formData.contactNumber} />
        {#if errors.contactNumber}<p class="error">{errors.contactNumber}</p>{/if}
    {/if}

    {#if step === 2}
        <input type="email" class="input-field" placeholder="Email..." bind:value={formData.email} />
        {#if errors.email}<p class="error">{errors.email}</p>{/if}

        <div class="date-time">
            <div class="date-container">
                <p>Start Date</p>
                <input type="date" class="input-field" bind:value={formData.startDate} />
                {#if errors.startDate}<p class="error">{errors.startDate}</p>{/if}
            </div>
            <div class="date-container">
                <p>End Date</p>
                <input type="date" class="input-field" bind:value={formData.endDate} />
                {#if errors.endDate}<p class="error">{errors.endDate}</p>{/if}
                {#if errors.dateRange}<p class="error">{errors.dateRange}</p>{/if}
                {#if errors.dateOverlap}<p class="error">{errors.dateOverlap}</p>{/if}
            </div>
        </div>
    {/if}

    {#if step === 3}
        <p>Enter Time</p>
        <input type="time" class="input-field" bind:value={formData.time} />
        {#if errors.time}<p class="error">{errors.time}</p>{/if}

        <select class="input-field" bind:value={formData.eventType}>
            <option disabled value="">Type of Event...</option>
        </select>
    {/if}

    <div class="buttons">
        {#if step > 1}
            <button class="cancel-button" on:click={previousStep}>Back</button>
        {/if}
        {#if step < 3}
            <button class="create-button" on:click={nextStep}>Next</button>
        {:else}
            <button class="create-button" on:click={submitForm}>Create Event</button>
        {/if}
        <button class="cancel-button" on:click={onClose}>Cancel</button>
    </div>
</div>
