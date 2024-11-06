<script>
    export let onClose;
    import './events.css';
</script>

<button class="modal-backdrop" on:click={onClose} aria-label="Close event form"></button>=
<div class="modal">
    <h2>Create Event</h2>
    <input type="text"  class="input-field" placeholder="Name..." />
    <input type="email"  class="input-field" placeholder="Email..." />
    <div class="date-time">
        <div class="date-container">
            <p>Start Date</p>
            <input type="date" class="input-field" placeholder="Start Date" />
        </div>
        <div class="date-container">
            <p>End Date</p>
            <input type="date" class="input-field" placeholder="End Date" />
        </div>
    </div>
    <p>Enter Time</p>
    <input type="time"  class="input-field" placeholder="Enter Time" />
    <select class="input-field" >
        <option>Type of Event...</option>
        <option>Sportfest</option>
        <option>Birthday</option>
        <option>Validation</option>
        <option>Exam</option>
        <option>Project Deadline</option>
    </select>
    <div class="buttons">
        <button class="create-button">Create Event +</button>
        <button class="cancel-button" on:click={onClose}>Cancel Event x</button>
    </div>
</div>