<script>
  import DownloadIcon from "./components/download.svelte";
  const CVlink = "assets/cv.pdf";
</script>

<style>
  section {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  a {
    text-decoration: none;
    width: 100%;
    display: flex;
    align-items: center;
    flex-direction: column;
    cursor: pointer;
  }
</style>

<section>
  <h2 class="Title">My CV</h2>
  <a href={CVlink} download="WilliamNordvist - CV/Personal Letter">
    <DownloadIcon size={'45'} color={'white'} />
  </a>
</section>
