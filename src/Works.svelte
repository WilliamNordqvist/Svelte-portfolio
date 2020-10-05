<script>
  import content from "../public/content.js";
  import OverLay from "./components/Overlay.svelte";
  import { mobile } from "./components/store.js";

  let spg = "assets/spg.png";
  let insurely = "assets/insurelykarta.png";
  let natten = "assets/natten.png";
  let selectedWork;
  let toggleOverlay = false;

  const openOverlay = work => {
    selectedWork = work;
    toggleOverlay = true;
  };

  const closeOverlay = () => {
    selectedWork = null;
    toggleOverlay = false;
  };
</script>

<style>
  section {
    z-index: 1;
    margin-bottom: 20em;
  }

  ul {
    margin: 3em auto;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .card {
    height: 14em;
    width: 24em;
    margin: 1em;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.12);
    overflow: hidden;
    transition: 0.3s all ease-in-out;
  }

  .cardImg {
    height: 100%;
    background-repeat: round;
    transition: 0.3s all ease;
  }

  .gradient {
    width: 100%;
    height: 100%;
    background: linear-gradient(
      180deg,
      rgba(0, 0, 0, 0.1),
      rgba(0, 0, 0, 0.7) 70%
    );
    transform: translateY(1000px);
    transition: 0.3s all ease-in-out;
  }

  .text {
    width: 100%;
    position: absolute;
    bottom: 30px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-transform: uppercase;
  }

  .title {
    color: #f9f1e9;
    font-weight: 400;
    letter-spacing: 0.1em;
  }

  button {
    text-transform: uppercase;
    background-color: transparent;
    border: 2px solid #f9f1e9;
    color: #f9f1e9;
    padding: 8px 25px;
    text-decoration: none;
    display: inline-block;
    margin: 4px 2px;
    transition-duration: 0.4s;
    cursor: pointer;
  }

  .card:hover {
    box-shadow: 0 1px 1px rgba(255, 255, 255, 0.1),
      0 2px 2px rgba(255, 255, 255, 0.1), 0 4px 4px rgba(255, 255, 255, 0.1),
      0 8px 8px rgba(255, 255, 255, 0.1), 0 16px 16px rgba(255, 255, 255, 0.1);
    transform: translateY(-2px);
  }
  .cardImg:hover {
    transform: scale(1.01);
  }

  .cardImg:hover > .gradient {
    transform: translateY(0);
  }

  button:hover {
    background-color: #f9f1e9;
    color: black;
  }
  button:focus {
    outline: 0;
  }

  @media only screen and (max-width: 768px) {
    .cardImg:hover > .gradient {
      transform: translateY(1000px);
    }
  }
</style>

<section>
  <h2 class="Title">My Work</h2>
  <ul class="cardsComponent">
    {#each content as work (work.name)}
      <div class="card" on:click={$mobile && (() => openOverlay(work))}>
        <div class="cardImg" style={`background-image:url(${work.img})`}>
          <div class="gradient">
            <div class="text">
              <h1 class="title">{work.name}</h1>
              <button on:click={() => openOverlay(work)}>Läs mer</button>
            </div>
          </div>
        </div>
      </div>
    {/each}
  </ul>
  <OverLay {selectedWork} {closeOverlay} {toggleOverlay} />
</section>
