<script>
import PasswordStrength from "./lib/PasswordStrength.svelte";

let password = "";

</script>

<div class="flex flex-col h-screen w-screen items-center justify-center bg-slate-200">
  <h2 class="mb-2 text-2xl font-bold text-gray-900">Insert a password</h2>
  <div class=" w-96 rounded-2xl overflow-hidden shadow-lg p-12 bg-white">
    <input type="password" placeholder="Password" class="w-full my-3 p-3 border-b-2 border-black" bind:value={password} />
    <PasswordStrength passwordValue={password}></PasswordStrength>
  </div>
</div>