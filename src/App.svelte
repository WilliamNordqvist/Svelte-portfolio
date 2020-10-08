<script>
  import Layout from "./Layout.svelte";
  import StarWars from "./StarWars.svelte";
  import Works from "./Works.svelte";
  import Skills from "./Skills.svelte";
  import CV from "./Cv.svelte";
  import Footer from "./Footer.svelte";

  import Background1 from "./Background.svelte";

  var isSafari =
    /constructor/i.test(window.HTMLElement) ||
    (function (p) {
      return p.toString() === "[object SafariRemoteNotification]";
    })(
      !window["safari"] ||
        (typeof safari !== "undefined" && safari.pushNotification)
    );
</script>

<style>
  .content-container {
    background: radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%);

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
    <Background1>
      <Layout>
        <StarWars />
      </Layout>
      <Works />
      <Skills />
      <CV />
    </Background1>
    <Footer />
  </div>
</main>
