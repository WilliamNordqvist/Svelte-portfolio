<script>
  import { onMount } from "svelte";

  let y;
  let startAt = 0;
  let elementToTop;
  let elementHeight;
  let start = false;

  onMount(() => {
    elementToTop = document.querySelector(".bars").offsetTop;
    elementHeight =
      document.querySelector(".bars").getBoundingClientRect().height / 2;
    startAt = elementToTop - window.innerHeight + elementHeight;

    return () => {
      elementToTop = 0;
      elementHeight = 0;
      startAt = 0;
    };
  });

  $: y > startAt ? (start = true) : null;

  const william = [
    { title: "HTML", skill: 80 },
    { title: "JS", skill: 70 },
    { title: "CSS", skill: 80 },
    { title: "React", skill: 85 },
    { title: "Angular", skill: 40 },
    { title: "Svelte", skill: 40 },
    { title: "Node.js", skill: 50 },
    { title: "SQL", skill: 30 }
  ];
</script>

<style>
  section {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .bars {
    width: 90%;
    transition: 2s all ease;
    -moz-transition: 2s all ease;
  }

  .bar {
    position: relative;
    background: rgba(255, 255, 255, 0.8);
    box-shadow: 0 1px 1px rgba(255, 255, 255, 0.1),
      0 2px 2px rgba(255, 255, 255, 0.1), 0 4px 4px rgba(255, 255, 255, 0.1),
      0 8px 8px rgba(255, 255, 255, 0.1), 0 16px 16px rgba(255, 255, 255, 0.1);
    height: 1.5em;
    margin: 0.3em 0 0.7em 0;
    border-radius: 5px;
    padding: 1px 1px 1px .5px;
    -moz-padding:1px 1px 1px 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .barText {
    margin: 0;
    color: white;
    font-weight: 400;
    font-size: 16px;
  }

  progress[value] {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    width: 100%;
    height: 100%;
  }

  progress[value]::-webkit-progress-bar {
    background-color: transparent;
  }
  progress[value]::-moz-progress-bar {
    background-color: black;
    border-radius: 5px;

  }

  progress[value]::-webkit-progress-value {
    background: black;
    border-radius: 5px;
    transition: all 1s cubic-bezier(.6,.04,.98,.34);
    -moz-transition: 2s all ease;
  }


  span {
    position: absolute;
    left: 5px;
    top: 5px;
    color: white;
    font-size: 14px;
    font-weight: 100;
  }

  .progress-bar {
    background-color: whiteSmoke;
    border-radius: 2px;
    box-shadow: 0 2px 3px rgba(0, 0, 0, 0.25) inset;
    display: flex;
    align-items: center;
    width: 100%;
    height: 100%;
    position: relative;
  }

  .progress-bar > span {
    background-color: blue;
    border-radius: 2px;
    display: block;
    text-indent: -9999px;
  }

  @media only screen and (max-width: 768px) {
    span {
      font-weight: 400;
    }
  }
</style>


<svelte:window bind:scrollY={y} />

<section class="skills">
  <h2 class="Title">My Skills</h2>
  <div class="bars">
    {#each william as i (i.title)}
      <div class="barContainer">
        <h3 class="barText">{i.title}</h3>
        <div class="bar">
          <span>{i.skill}%</span>
          <progress max="100" value={start ? i.skill : 0}>
            <div class="progress-bar">
              <span style={`width: ${i.skill}%;`}>Progress:{i.skill}%</span>
            </div>
          </progress>
        </div>
      </div>
    {/each}
  </div>
</section>
