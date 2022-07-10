<script>
import { afterUpdate } from 'svelte';
import z from 'zxcvbn';

export let passwordValue;

let calculatedPasswordStrength = 0

afterUpdate(() => {
    const score = z(passwordValue).score + 1;
    calculatedPasswordStrength = score * 20;
});
</script>

<div class=" mt-2">
    <div class="w-full bg-gray-200 h-2 rounded-md">
        {#if passwordValue}
            {#if calculatedPasswordStrength <= 20}
            <div class="bg-red-600 h-2 rounded-md" style="width: 20%"></div>
            <div class=" text-right text-red-600">Very Weak!</div>
            {:else if calculatedPasswordStrength === 40}
            <div class="bg-amber-500 h-2 rounded-md" style="width: 40%"></div>
            <div class=" text-right text-amber-500">Weak!</div>
            {:else if calculatedPasswordStrength === 60}
            <div class="bg-lime-400 h-2 rounded-md" style="width: 60%"></div>
            <div class=" text-right text-lime-400">Normal!</div>
            {:else if calculatedPasswordStrength === 80}
            <div class="bg-green-500 h-2 rounded-md" style="width: 80%"></div>
            <div class=" text-right text-green-500">Good!</div>
            {:else if calculatedPasswordStrength === 100}
            <div class="bg-green-700 h-2 rounded-md" style="width: 100%"></div>
            <div class=" text-right text-green-700">Very Good!</div>
            {/if}
        {:else}
        <div class="bg-slate-800 h-2 rounded-md" style="width: 0%"></div>
        {/if}
    </div>
</div>
    