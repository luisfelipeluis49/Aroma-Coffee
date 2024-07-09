<script>
    // -- IMPORTS

    import Fa from "svelte-fa";
    import { faBell, faCircleQuestion, faMagnifyingGlass } from "@fortawesome/free-solid-svg-icons";
</script>

<style lang="stylus">
    header
    {
        position: fixed;
        top: 0;

        height: 7vh;
        width: 98vw;
        padding: 0 1vw;

        display: flex;
        flex-direction: row;
        justify-content: space-between;

        text-align: center;
        color: white;

        button
        {
            background-color: transparent;
            border: none;
        }
    }

    .toolbar
    {
        display: flex;
        flex-direction: row;
        gap: 1rem;
        align-items: center;
    }

    .search
    {
        padding: 0.5rem;
        border: 1px solid #333;
        border-radius: 0.5rem;

        display: flex;
        flex-direction: row;
        gap: 0.5rem;
        align-items: center;

        input
        {
            border: none;
            
            background-color: transparent;

            color: #333;
        }
    }

    .divider
    {
        height: 2rem;
        border-left: 1px solid #333;
    }

    .profile-image
    {
        width: 2rem;
        border-radius: 50%;
    }
</style>

<header>
    <button>
        <img src="images/logo.svg" alt="">
    </button>
    <div class="toolbar">
        <div class="search">
            <Fa icon={ faMagnifyingGlass } color="#333"/>
            <input type="text">
        </div>
        <Fa icon={ faCircleQuestion } color="#333"/>
        <div class="divider" />
        <Fa icon={ faBell } color="#333"/>
        <img src="https://picsum.photos/200" alt="" class="profile-image">
    </div>
</header>

