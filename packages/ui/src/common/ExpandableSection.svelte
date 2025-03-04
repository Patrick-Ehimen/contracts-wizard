<!-- ExpandableSection.svelte -->
<script lang="ts">
    import ToggleRadio from '../common/inputs/ToggleRadio.svelte';
    import HelpTooltip from '../common/HelpTooltip.svelte';
    
    export let label: string;
    export let type: 'checkbox' | 'toggleradio' = 'checkbox';
    export let checked: boolean | undefined = undefined;
    export let value: string | undefined = undefined;
    export let defaultValue: string | undefined = undefined;
    export let helpContent: string;
    export let helpLink: string;
    export let disabled = false;
    
    // Keep track of expanded state separately from checkbox state
    let isExpanded = false;
    
    function toggleExpanded() {
        isExpanded = !isExpanded;
    }
    </script>
    
    <section class="controls-section">
        <h1>
            <!-- svelte-ignore a11y-label-has-associated-control -->
            <label class="flex items-center tooltip-container pr-2">
                <span>{label}</span>
                <span class="ml-1">
                    {#if type === 'checkbox'}
                        <input
                            type="checkbox"
                            bind:checked={checked}
                            disabled={disabled}
                        >
                    {:else if type === 'toggleradio'}
                        <ToggleRadio
                            bind:value={value}
                            {defaultValue}
                            disabled={disabled}
                        />
                    {/if}
                </span>
                <!-- Button controls expansion/collapse independently -->
                <button
                    on:click|preventDefault={toggleExpanded}
                    class="mx-2 px-1"
                    aria-label={isExpanded ? "Collapse section" : "Expand section"}
                >
                    {isExpanded ? '▲' : '▼'}
                </button>
                <HelpTooltip align="right" link={helpLink}>
                    {helpContent}
                </HelpTooltip>
            </label>
        </h1>
        
        {#if isExpanded}
            <div class="expandable-content">
                <slot />
            </div>
        {/if}
    </section>
    
    <style>
    .expandable-content {
        padding-left: 1.5rem;
        margin-top: 0.5rem;
        border-left: 2px solid #e2e8f0;
    }
    </style>