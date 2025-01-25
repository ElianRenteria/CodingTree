<main class="container">
    <article>
        <h1>Register</h1>
        <input type="email" name="email" placeholder="Email" aria-label="Email" autocomplete="email">
        <input type="password" name="password" placeholder="Password" aria-label="Password">
        <input type="password" name="password" placeholder="Confirm Password" aria-label="Password">
        <button>Register</button>
        <a href="/signin">Sign in</a>
    </article>
</main>

<style>
    .container {
        margin-top: 2rem;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    article {
        width: 40%;
        min-width: 500px;
        min-height: 600px;
        padding-top: 5rem;
        padding-left: 4rem;
        padding-right: 4rem;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1rem;
    }
    a {
        margin-top: 2rem;
        margin-bottom: 1rem;
    }
    button{
        margin-top: 1rem;
        border-radius: 3rem;
        padding-left: 4rem;
        padding-right: 4rem;
    }
</style>