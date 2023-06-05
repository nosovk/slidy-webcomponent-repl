<script lang="ts">
  import '../../lib';
</script>

<main>
  <h1>Slidy wrapped in webcomponent!</h1>
  <p>Visit the <a href="https://www.npmjs.com/package/@slidy/core">Slidy doc</a> to learn how to build slidy wrapper.</p>

  <p class="container">
    <my-component>
      <ul slot="slides">
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1573969697766-0e78459ae043?w=804"/>
        </li>
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1570231208815-a8a53ff11b36?w=1824"/>
        </li>
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1542879418-c6c556ff5690?w=1800"/>
        </li>
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1477592954047-28a31ae67583?w=1920"/>
        </li>
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1573969697766-0e78459ae043?w=804"/>
        </li>
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1570231208815-a8a53ff11b36?w=1824"/>
        </li>
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1542879418-c6c556ff5690?w=1800"/>
        </li>
        <li>
          <img
                  loading="lazy"
                  src="https://images.unsplash.com/photo-1477592954047-28a31ae67583?w=1920"/>
        </li>
      </ul>
      <div slot="nav">nav text</div>
    </my-component>
  </p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    font-size: 4em;
    line-height: 1.1;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }

    .container {
      display: inline-block;
      max-width: 320px;
    }
  }
</style>
