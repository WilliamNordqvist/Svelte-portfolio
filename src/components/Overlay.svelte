<script>
  import CloseIcon from "./closeIcon.svelte";
  export let selectedWork;
  export let closeOverlay;
  export let toggleOverlay;

  const githubImg = "assets/GitHub-Mark-64px.png";
  const webLink = "assets/www.png";
</script>

<style>
  .section {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    overflow: scroll;
    opacity: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: 0.5s all ease-in-out;
  }
  .contentContainer {
    position: relative;
    width: 90%;
    height: 90%;
    background: rgba(240, 240, 240, 0.99);
    border-radius: 5px;
    overflow: scroll;
  }

  .close {
    position: absolute;
    right: 10px;
    top: 10px;
    cursor: pointer;
  }

  .content {
    margin-top: 4em;
    text-align: center;
  }

  h1 {
    text-transform: uppercase;
    font-weight: 400;
    font-size: 3em;
  }

  hr {
    width: 80%;
  }

  .workImg {
    width: 80%;
  }

  .contentText {
    width: 80%;
    margin: 2em auto;
    line-height: 1.4;
    text-align: center;
    color: #333;
  }

  .githubImg {
    width: 2em;
    cursor: pointer;
  }

  .visistLink {
    text-decoration: none;
  }

  .visistLink:hover {
    text-decoration: underline;
  }
  @media only screen and (max-width: 768px) {
    .contentContainer {
      width: 100%;
      height: 100%;
      border-radius: 0;
    }
    h1 {
      font-size: 2em;
    }
    .workImg {
      width: 100%;
    }
    .contentText {
      width: auto;
      margin: 0;
      text-align: center;
      padding: 0px 1em;
    }
  }
</style>

<div
  class="section"
  style={`opacity:${toggleOverlay ? '1' : '0'}; z-index:${toggleOverlay ? '1' : '-1'}`}>
  <div class="contentContainer">
    <div class="close" on:click={() => closeOverlay()}>
      <CloseIcon size="1.2em" />
    </div>
    {#if selectedWork}
      <div class="content">

        <a target="_blank" rel="noopener noreferrer" href={selectedWork.link}>
          <img
            class="workImg"
            src={selectedWork.img}
            alt={`image of ${selectedWork.name}`} />
        </a>
        <h1>{selectedWork.name}</h1>

        <hr>

        <div class="contentText">
          {@html selectedWork.description}
        </div>
        {#if selectedWork.github !== null}
          <a
            target="_blank"
            rel="noopener noreferrer"
            href={selectedWork.github}>
            <img class="githubImg" src={githubImg} alt="github-link" />
          </a>
        {/if}
        <p>
          <b>
            <a
              target="_blank"
              rel="noopener noreferrer"
              class="visistLink"
              href={selectedWork.link}>
              {selectedWork.link}
            </a>
          </b>
        </p>
      </div>
    {/if}

  </div>
</div>
