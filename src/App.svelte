<script>
  import Layout from "./Layout.svelte";
  import StarWars from "./StarWars.svelte";
  import Works from "./Works.svelte";
  import Skills from "./Skills.svelte";
  import CV from "./Cv.svelte";
  import Footer from "./Footer.svelte";

  var isSafari =
    /constructor/i.test(window.HTMLElement) ||
    (function(p) {
      return p.toString() === "[object SafariRemoteNotification]";
    })(
      !window["safari"] ||
        (typeof safari !== "undefined" && safari.pushNotification)
    );
  $: console.log(window.scrollY);
</script>

<style>
  .content-container {
    /* overflow: scroll; */
    background: url(https://cdn.pixabay.com/photo/2016/11/23/15/23/cosmos-1853491_1280.jpg);

    overflow: hidden;
    -webkit-background-size: contain;
    -moz-background-size: contain;
    -o-background-size: contain;
    background-size: contain;
    background-position: center center;
    scroll-behavior: smooth;
  }

  @media only screen and (max-width: 768px) {
    .content-container {
      -webkit-background-size: auto;
      -moz-background-size: auto;
      -o-background-size: auto;
      background-size: auto; 
    }
  }
</style>

<main>

  <div
    style={`background-attachment:${isSafari ? 'scroll' : 'fixed'}`}
    class="content-container">
    <Layout>
      <StarWars />
    </Layout>
    <Works />
    <Skills />
    <CV />
    <Footer />

  </div>

</main>
