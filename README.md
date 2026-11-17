# Ewing Gallery: Art, Movement, and Disability (virtual gallery)

A small digital collection of selected works from *Art, Movement, and Disability: Transcending the Beauty Paradigm*, a fall 2026 exhibition at the Ewing Gallery of Art + Architecture, University of Tennessee, Knoxville.

The site is built with [CollectionBuilder-GH](https://github.com/CollectionBuilder/collectionbuilder-gh) and published with GitHub Pages.

## Where things live

| What | File |
| --- | --- |
| Collection metadata (one row per artwork) | `_data/Ewing-Gallery-MTP-Sheet1.csv` |
| Artwork images | `objects/` |
| Site title, tagline, description | `_config.yml` |
| Home page image, colors, page options | `_data/theme.yml` |
| Navigation menu | `_data/config-nav.csv` |
| About page text | `pages/about.md` |

## Adding an artwork

1. **Prepare the image.** Resize it to about 2400px on the long edge and strip the camera metadata, which includes GPS location. With ImageMagick:

   ```sh
   convert original.jpg -auto-orient -resize '2400x2400>' -strip -quality 82 objects/NN-Title.jpg
   ```

2. **Add a row** to `_data/Ewing-Gallery-MTP-Sheet1.csv`:
   - `objectid`: unique, no spaces (e.g. `12-Untitled`)
   - `filename`: the exact image file name in `objects/`
   - `title`, `creator`, `date` (a year such as `2020`)
   - `description`: the catalog description, including the medium from the wall label
   - `image_alt_text`: a visual description for screen-reader users. Say what is actually visible: shapes, colors, layout, and any text in the image.
   - `subject`: keywords separated by `;` (e.g. `sculpture;plaster`)
   - `type`: `Image` for 2D work, `Physical Object` for sculpture
   - `format`: `image/jpeg`

   Don't leave placeholder rows with only an `objectid`. They create empty item pages.

3. Commit and push. GitHub Pages rebuilds the site in a minute or two.

## Previewing locally

```sh
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000>.

## Credits and license

Built on [CollectionBuilder](https://collectionbuilder.github.io/) from the University of Idaho Library. Template code is MIT licensed (see `LICENSE`).
The artworks belong to their artists and are **not** covered by that license.
