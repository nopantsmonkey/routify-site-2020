<script>

  import { tick, onMount } from "svelte";
  import { meta } from "@sveltech/routify";
  import {default as Prism, highlight} from "svelte-prism";
  import "prismjs/plugins/command-line/prism-command-line.js";
  import "prismjs/components/prism-bash";
  import "prismjs/components/prism-json";

  meta.title = "Basics";
</script>

<div class="c-content">
  <h1>Configuration</h1>
  <p>Routify can be configured with the following options.</p>
</div>

<table class="c-table c-table--styled">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Default value</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>debug</td>
    <td>boolean</td>
    <td>
      <code>false</code>
    </td>
    <td>Show extra debug information</td>
  </tr>
  <tr>
    <td>pages</td>
    <td>string</td>
    <td>
      <code>./src/pages</code>
    </td>
    <td>Path to pages.</td>
  </tr>
  <tr>
    <td>ignore</td>
    <td>array|string</td>
    <td>None</td>
    <td>Files and dirs to be ignored. Interpreted as regular expression.</td>
  </tr>
  <tr>
    <td>unusedPropWarnings</td>
    <td>boolean</td>
    <td>
      <code>false</code>
    </td>
    <td>Show warnings about unused props passed by filerouter.</td>
  </tr>
  <tr>
    <td>dynamicImports</td>
    <td>boolean</td>
    <td>
      <code>false</code>
    </td>
    <td>Enable code splitting.</td>
  </tr>
  <tr>
    <td>singleBuild</td>
    <td>boolean</td>
    <td>
      <code>false</code>
    </td>
    <td>Don't watch for file changes.</td>
  </tr>
</table>


<h2 class="c-h2">To use with CLI</h2>
<pre  class="command-line" data-output="2-18">
  <code use:highlight class="language-bash">
    {`
        npx @sveltech/routify --help
        Usage: cli [options] [command]

        Options:
        -d, --debug                    extra debugging
        -p, --pages &#60;location>         path/to/pages (default: "src/pages")
        -i, --ignore &#60;list>            Files and dirs. Can be string or array. Interpreted as regular expression (default: [])
        -u, --unused-prop-warnings     Show warnings about unused props passed by filerouter (default: true)
        -D, --dynamic-imports          Code splitting) (default: false)
        -b, --single-build             Don't watch for file changes (default: false)
        -s, --scroll [behavior]        Scroll behavior (default: "smooth")
        -e, --extensions &#60;names>       Included file extensions (comma separated) (default: ["html","svelte","md"])
        -c, --child-process &#60;command>  Run command when Routify is ready
        -h, --help                     output usage information

        Commands:
        init
        export [options]
  `}
  </code>
</pre>
<!-- </Prism> -->

<h2 class="c-h2">CLI + Sirv example</h2>


<Prism language="json">
  {`/** package.json **/
...
"scripts": {
  "debug:routify": "routify -du --pages ./src/path/to/pages",
  "start:routify": "routify --pages ./src/path/to/pages",
  "dev:start": "run-p debug:routify start:sirv autobuild",
  ...
}
`}
</Prism>