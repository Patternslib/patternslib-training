# 1.6 - Integrating other patterns

Integrating patterns from other bundles can be done as described in <a href="./1.01/index.md" class="pat-inject">1.1 - Integrate more bundles</a>.

In a breeze, add the `remote.min.js` from that other bundle like so:


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Patternslib training</title>
    <script>
      window.__patternslib_disable_modernizr = true;
      window.__patternslib_import_styles = true;
    </script>
    <script src="https://cdn.jsdelivr.net/npm/@patternslib/patternslib@9.8.0-beta.6/dist/bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@patternslib/pat-leaflet@2.1.0/dist/remote.min.js"></script>
  </head>
  ...
```

And then use a pattern from that bundle. In this case, pat-leaflet:


<div class="pat-clone-code">
<div
    style="height:400px"
    class="pat-leaflet"
    data-pat-leaflet="
        fullscreencontrol: true;
        locatecontrol: true;
        zoomcontrol: true;
        minimap: true;
        geosearch: true;
        geosearch_provider: nominatim;
        addmarker: true;
        maxClusterRadius: 80;
    "
></div>
</div>

