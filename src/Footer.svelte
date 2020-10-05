<script>
  import LinkedInSVG from "./components/linkedin.svelte";
  import GithubSVG from "./components/github.svelte";
  import GmailSVG from "./components/gmail.svelte";

  const size = "35";
  const color = "white";
</script>

<style>
  footer {
    position: relative;
    background: linear-gradient(
      180deg,
      rgba(0, 0, 0, 0) 2%,
      rgba(0, 0, 0, 1) 50%
    );
    margin-top: 20em;
    padding-top: 15em;
  }

  .iconsContainer {
    position: absolute;
    bottom: 5em;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .iconBorder {
    cursor: pointer;
    margin: 0 0.8em;
  }
</style>

<footer>
  <div class="iconsContainer">

    <a target="_blank" rel="noopener noreferrer" href="https://www.linkedin.com/in/william-nordqvist-7221b340/">
      <div class="iconBorder">
        <LinkedInSVG {size} {color} />
      </div>
    </a>

    <a target="_blank" rel="noopener noreferrer" href="https://github.com/WilliamNordqvist">
      <div class="iconBorder">
        <GithubSVG {size} {color} />
      </div>
    </a>


    <a href="mailto:wnordqvist@gmail.com">
      <div class="iconBorder">
        <GmailSVG {size} {color} />
      </div>
    </a>

  </div>
</footer>
