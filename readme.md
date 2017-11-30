# Webgem code, testing en oplevering
Dit bestand bevat alle regels die door ons zijn afgesproken op gebied van code, code quality, testing, oplevering en wijzigingen in de productie versie.

## Code guidelines
---
De guidelines die op toepassing zijn op de verschillende code bestanden die wij gebruiken.

### *JavaScript*
Wij maken gebruik van de [Airbnb JavaScript Style Guide.](https://github.com/airbnb/javascript)<br>

Documenteer elke functie:
- Wat doet het
- Waar wordt het uitgevoerd
- De props die functie accepteerd en wat voor props dit zijn.

### *CSS*
De basis style guide van onze CSS is [Airbnb CSS / Sass Styleguide](https://github.com/airbnb/css).<br>

#### Mappen structuur
Wij hanteren een vaste mappen structuur.<br>
```
  dev/
    css/
      style.scss
      parts/
        reset.scss
        vars.scss
        global.scss
        pagename.scss

```
- style.scs *Hierin wordt geen css zelf in geschreven alleen de parts geimporteerd.*

- reset.scss *Onze basis reset.scss is gebaseert op [Reset CSS](https://meyerweb.com/eric/tools/css/reset/).*
- vars.scss *Hier worden alle variables gedefineerd.*
- global.scss *Css die op alle pagina's gericht is of gericht op elementen die op meerdere pagina's worden toegepast.*
- pagename.scss *Pagina specifieke code maak de bestandnaam de naam van de pagina waar de css relevant voor is.*

#### Overige Style Guide CSS
Probeer ID's te vermijden.
```css
  /* bad */
  #homepage{
    background: #fafafa;
  }

  /* good */
  .homepage{
    background: #fafafa;
  }
```
Classname's moeten logisch zijn.
```css
  /* bad */
  .blockiehome{
    background: #fafafa;
  }

  .asf1{
    background: #fafafa;
  }

  /* good */
  .home{
    background: #fafafa;
  }

  /* bad */
  /* vermijd nummers in classnames */
  .foo1, .foo2, .foo3{
    background: #fafafa;
  }

  /* good */
  /* geef de sectie ook een naam die de sectie omschrijft. */
  .foo{
    background: #fafafa;
  }
```

Don't repeat yourself.
```css
  /* bad */
  .foo{
    display: flex;
    flex-direction: column;
    top: 100px;
    background: #fafafa;
  }
  .bar{
    display: flex;
    flex-direction: column;
    top: 100px;
    background: #fefefe;
  }
  .baz{
    display: flex;
    flex-direction: column;
    top: 100px;
    background: #fdfdfd;
  }

  /* good */
  .foo,
  .bar,
  .baz{
    display: flex;
    flex-direction: column;
    top: 100px;
  }

  .foo{
    background: #fafafa;
  }

  .bar{
    background: #fefefe;
  }

  .baz{
    background: #fdfdfd;
  }
```

Prefix classes die voor javascript zijn gemaakt met js-
```css
  /* bad */
  .dropdown{
    display: none;
    ...
  }

  .open{
    display: block;
  }

  /* good */
  .dropdown{
    display: none;
    ...
  }

  .js-open{
    display: block;
  }
```

maak eigenschappen gesorteerd op a-z
```css
  /* bad */
  .foo{
    display: flex;
    flex-direction: column;
    position: fixed;
    top: 100px;
    left: 0;
    background: #fafafa;
    width: 100%;
    align-items: flex-start;
    flex-wrap: nowrap;
    padding: 0 5%;
    margin: 0;
    z-index: 1;
    height: 0;
    overflow: hidden;
    justify-content: center;
  }

  /* good */
  .foo{
    align-items: flex-start;
    background: #fafafa;
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    height: 0;
    justify-content: center;
    left: 0;
    margin: 0;
    overflow: hidden;
    padding: 0 5%;
    position: fixed;
    top: 100px;
    width: 100%;
    z-index: 1;
  }
```

### *Html*
The html styling rules for our html.
We gebruiken [Google's styleguide](https://google.github.io/styleguide/htmlcssguide.html) als een basis voor onze html style guide.

#### Indentation
Gebruik 2 spaties.
```html
  <nav>
    <a href="example">example</a>
    <a href="example">example</a>
    <a href="example">example</a>
  </nav>
```

Voorkom trailing whitespaces.
```html
  <!-- bad -->
  <p>Dit is een zin._

  <!-- good -->
  <p>Dit is een zin.
```

#### Images
geef een waardevolle alt tag
```html
  <!-- bad -->
  <img src="example.png" alt="afbeelding example">
  <!-- Alt tags zijn niet gemaakt om al je seo tags in te plaatsen -->
  <img src="example.png" alt="example, keyword1, keyword2, keyword3">

  <!-- good -->
  <img src="example.png" alt="Omschrijving van de afbeelding">
```
Als nodig gebruik sizes en srcset
```html
  <img
    src="example-mid.png"
    srcset="
      example-small.png 300w,
      example-mid.png 500w,
      example-big.png 1000w
    "
    sizes="
      (max-width: 300px) 100vw,
      500px
    "
    alt="Omschrijving van de afbeelding"
  >
```

#### Paragraph tag
geen newline bij p
```html
  <!-- bad -->
  <p>
    Hallo dit is een zin.
  </p>

  <!-- good -->
  <p>Hallo dit is een zin.</p>
```
Geen dubbele breaks voor witte regel
```html
<!-- bad -->
<p>Dit is een example tekst hier wat lorem ipsum.
<br><br>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla pharetra eu metus sit amet sagittis. Donec nec velit quis diam hendrerit consectetur. Quisque lacinia eu sapien nec interdum. Nullam quis commodo enim. Proin ut feugiat elit.
<br><br>
Vestibulum consectetur erat justo, eget tempor nunc convallis rhoncus. Donec nec purus efficitur, pulvinar libero eu, accumsan odio. Mauris enim lacus, placerat ac lectus id, congue pretium est. Vestibulum porta lobortis dolor, scelerisque varius metus tincidunt at. Sed ornare lacus ultrices consectetur suscipit. Duis vulputate elementum ante, et commodo nibh tempor nec.
</p>

<!-- good -->
<p>Dit is een example tekst hier wat lorem ipsum.</p>

<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla pharetra eu metus sit amet sagittis. Donec nec velit quis diam hendrerit consectetur. Quisque lacinia eu sapien nec interdum. Nullam quis commodo enim. Proin ut feugiat elit. </p>

<p>Vestibulum consectetur erat justo, eget tempor nunc convallis rhoncus. Donec nec purus efficitur, pulvinar libero eu, accumsan odio. Mauris enim lacus, placerat ac lectus id, congue pretium est. Vestibulum porta lobortis dolor, scelerisque varius metus tincidunt at. Sed ornare lacus ultrices consectetur suscipit. Duis vulputate elementum ante, et commodo nibh tempor nec.</p>
```

## Testing
---
De guidelines van het testen van code. **Test alle code online op een test server niet local.**
### *UI*
Probeer de code automatisch te testen met [galen framework](http://galenframework.com/).

Test de website in alle moderne browsers, en oudere browsers die door de doelgroep worden gebruikt.

Test de website op verschillende apparaten en beeldscherm grotes.

### *Code quality*
Valideer alle html in de [html validator](https://validator.w3.org/) en valideer alle css in de [CSS validator](https://jigsaw.w3.org/css-validator/).

Maak in github een pull request met de door jou aangepaste code.
Omschrijf in de pull request wat de code doet.

Assign iemand anders van het team als een reviewer en laat iemand anders het reviewen voordat de code wordt gemerged.

### *Review checklist*
Werk deze checklist af bij reviewen van de code.
- Is de code gevalideert.
- Voldoet de code aan de style guides.
- Is de code een efficiente manier om het te doen.
- Breekt de code andere elementen in de website.
- Zijn er bugs die door deze code ontstaan.
- Gebruikt de code de laatste versie van de al bestaande code.


## Oplevering
---
Zorg dat alle code getest is zoals hierboven is aangegeven.

### *Changelog*
Maak een changelog waarin alle aanpassingen in deze (nieuwe)versie staan.<br>
Deze changelog of een samenvatting ervan zou zo naar de klant gestuurd moeten kunnen worden, gebruik dus termen die de klant begrijpt.

### *Backup*
Als er al een online versie van het product online staat, maak dan een backup van de gehele site.

Zodat als er iets misgaat in de nieuwe versie wij de oude versie terug kunnen zetten.

### *Uploaden van nieuwe versie*
Nadat de backup klaar is kan de nieuwe versie worden geupload.

Zodra de nieuwe versie online staat meldt dit aan het team, zodat de nieuwe online versie kan worden getest.