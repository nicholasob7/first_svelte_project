<script>
    import { createEventDispatcher } from "svelte";
    // import { fly } from "svelte-transition";
    const dispatch = createEventDispatcher();

    export let user;
    export let i;

    

    const remove = () => {
        dispatch("remove", user.id);
    };

</script>

<div
    class="flex m-5 bg-blue
    border p-2 rounded-lg shadow-md 
    hover:shadow-lg cursor-pointer items-center relative"
>
    <button
        on:click={remove}
        class="absolute right-0 top-0 -mt-3
    rounded-full bg-red-300 w-5 h-5 text-center text-white text-sm
    hover:bg-red-700"
        >X
    </button>
    <p class="w-10">{i + 1}</p>
    <img class="rounded-full w-14 h-14" src={user.image} alt={user.name} />
    <p class="mx-4 w-25">{user.name}</p>
    <p class="mx-4 w-25">{user.email}</p>
</div>
