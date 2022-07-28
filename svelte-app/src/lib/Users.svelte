<script>
    import Nicholas from "../assets/images/Nicholas.jpg";
    import SamPlace from "../assets/images/SamPlace.jpg";
    import NickCPlace from "../assets/images/NickCPlace.jpg";
    import User from "./User.svelte";
    import FilterUser from "./FilterUser.svelte";
    import NewUser from "./NewUser.svelte";

    let users = [
        {   id: 1,
            image: Nicholas,
            name: "Nicholas O'Brien",
            email: "obrien06@myunitec.ac.nz",
            active: true,

        },
        { 
            id: 2,
            image: SamPlace,
            name: "Sameera Begum",
            email: "Samebeg@yahoo.com",
            active: true,

        },
        { 
            id: 3,
            image: NickCPlace,
            name: "Nick Chitsamrerng",
            email: "imnickdev@gmail.com",
            active: false,

        },
    ];

    $: filteredUsers = users;

    const filter = ({detail}) => {
        if (detail === "null"){
            filteredUsers = users;
            return;
        }
        const active = detail === "true";
        filteredUsers = users.filter((user) => user.active
        === active);
    };

    const remove =({detail}) => {
        users = users.filter((user) => user.id !== detail);
        
    };
</script>

<div>
    <h1 class="text-2xl text-center mt-10">List of Users</h1>

    <FilterUser on:filter={filter} />
    <NewUser />

    {#each filteredUsers as user, i (user.id)}
        <User on:remove={remove} {user} {i} />
    {:else}
        <p>No user found</p>
    {/each}
</div>
