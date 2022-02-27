<script>
  let earlyAccessSet = false;

  function signUpEarlyAccess(e) {
    let formData = new FormData(e.target);
    fetch("/", {
      method: "POST",
      headers: {"Content-Type": "application/x-www-form-urlencoded"},
      body: new URLSearchParams(formData).toString()
    }).then(() => earlyAccessSet = true).catch((error) => console.log("Error: ", error))
  }

  let newsLetterSet = false;

  function signUpNewsletter(e) {
    let formData = new FormData(e.target);
    fetch("/", {
      method: "POST",
      headers: {"Content-Type": "application/x-www-form-urlencoded"},
      body: new URLSearchParams(formData).toString()
    }).then(() => newsLetterSet = true).catch((error) => console.log("Error: ", error))
  }
</script>

<main>
    <h1 id="because-you-can-do-more-than-debugging">Because you can do more
        than debugging…</h1>
    <p>CodersWhoDesign is a community of developers who want to redefine
        what a developer is capable of.</p>
    <h2 id="where-does-software-design-belong">Where does software design
        belong?</h2>
    <p>Great architects build our physical world, software developers do the
        same thing for our virtual world.</p>
    <p>However, often this world tries to convince us that we are just here to
        write code like a cog in machine and incapable of thinking about good
        design. An external consultant dictates how the software should look,
        this results in an awful developer and user experience.</p>
    <p>The problem is, some of us accept this reality and limit themselves.
        This make us feel sad and want to change this.</p>
    <h2 id="is-this-community-for-you">Is this community for you?</h2>
    <p>We could not find a place where people come together, share their
        experiences and work on projects to level up. There are many blogs,
        tutorials, forums and Udemy classes, but they seldom help us move
        forward. That is the reason why this idea came.</p>
    <p>This is not about self-promotion or disconnected discussion, but
        about connections, trust and progress towards a reality where we take
        ownership of software making.</p>
    <h2 id="why-projects">Why projects?</h2>
    <p>Project based learning helps people focus on the key elements of
        software engineering, and it is also much more fun! Shipping a real
        product to real users motivate us and help to be really pragmatic. You
        give feedback and you can get feedback.</p>
    <h2>Where are we standing with this community?</h2>
    <p>We are at the beginning of
        the journey. In the next step we want to design a workshop. Nothing
        fancy. We need to define projects, timelines and the way we will
        interact with each other.</p>
    <p>If this resonates with you, and you are either an experienced or
        aspiring software maker, come help us shape this community.</p>

    {#if earlyAccessSet}
        <p>Thanks!</p>
    {:else}
        <form on:submit|preventDefault={signUpEarlyAccess}
              name="earlyaccess"
              data-netlify="true"
              method="POST"
              data-netlify-honeypot="bot-field"
        >
            <input type="hidden" name="form-name" value="earlyaccess"/>
            <input type="email" placeholder="Your email" name="email" required/>
            <button type="submit">I am in!</button>
        </form>
    {/if}

    {#if newsLetterSet}
        <p>Thank you!</p>
    {:else}
        <p>Just want to get updates for now?</p>
        <form on:submit|preventDefault={signUpNewsletter}
              name="newsletters"
              method="POST"
              data-netlify="true"
              data-netlify-honeypot="bot-field"
        >
            <input type="hidden" name="form-name" value="newsletters"/>
            <input type="email" placeholder="Your email" name="email" required/>
            <button type="submit">Send me only updates</button>
        </form>
    {/if}

</main>

<style>
    :root {
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
        Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-size: 16px;
        color: #334155;
        background-color: #fff7ed;
        --primary-color: #ea580c; /* orange  600*/
    }

    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        max-width: none;
    }

    main {
        text-align: center;
        margin: 0 auto;
    }


    h1 {
        font-size: 2.5rem;
        font-weight: 800;
        margin: 3rem auto;
    }

    h2 {
        font-size: 2rem;
        font-weight: 600;
        margin-block-start: 3rem;
        margin-block-end: 2rem;
    }

    p {
        margin: 1rem auto;
        font-size: 1.1875rem;
        line-height: 1.35;
    }

    h1, h2 {
        color: var(--primary-color);
        line-height: 1;
    }

    input {
        font-size: 1.2rem;
        padding: 1rem 1rem;
        -webkit-appearance: none;
        appearance: none;
        box-shadow: none;
        border: none;
        border-radius: 0.3rem;
    }

    button {
        font-size: 1.2rem;
        padding: 1em 2em;
        color: #fff;
        background-color: var(--primary-color);
        outline: none;
        font-variant-numeric: tabular-nums;
        cursor: pointer;
        background-image: none;
        -webkit-appearance: none;
        appearance: none;
        box-shadow: none;
        border: none;
        border-radius: 0.3rem;
    }

    input, button {
        display: block;
        width: 100%;
        margin-block: 1rem;
    }

    form {
        padding-inline: 1rem;
        padding-block-end: 2rem;
    }

    @media (min-width: 480px) {
        h1 {
            font-size: 3rem;
        }

        h1, h2, p, form {
            max-width: 42rem;
            margin-inline: auto;
        }

        form {
            padding-inline: 4rem;
            padding-block-end: 4rem;
        }
    }
</style>
