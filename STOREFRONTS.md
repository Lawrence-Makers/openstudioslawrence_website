# Storefront YAML Reference

Each storefront is a `.yaml` file in `data/storefronts/`. Files are displayed in alphabetical order by filename, so prefix them with `01-`, `02-`, etc. to control order.

---

## Fields

### `locationName` *(required)*
The name of the storefront, displayed as the large heading.
```yaml
locationName: "The Livingroom Collective"
```

---

### `address1` / `address2`
Street address and city/state/zip, displayed below the name.
```yaml
address1: "938 Massachusetts St"
address2: "Lawrence, KS 66044"
```

---

### `hoursHeading`
Replaces the default "Hours" label above the hours list. Accepts HTML. Useful for a status message when no regular hours exist yet.
```yaml
hoursHeading: "<i>Coming Soon!</i>"
```
If omitted and `hours` is present, defaults to **"Hours"**.

---

### `hours`
List of hour strings shown below the hours heading. Accepts HTML in each entry.
```yaml
hours:
  - "Thursday: 11am to 7pm"
  - "Friday: 11am to 7pm"
  - "Saturday: 9am to 3pm"
  - "Sunday: 11am to 3pm"
  - "<i>Open through the end of August!</i>"
```

---

### `events`
List of upcoming special events, displayed in a column to the right of hours (or on their own if no hours). Accepts HTML.
```yaml
events:
  - "Grand Opening: July 31 (Final Friday) 5–9pm"
  - "Burlesque Show: August 15, 8pm"
```

---

### `photo`
Path to the storefront photo, relative to `static/`. Displayed below the hours/events.
```yaml
photo: "/images/storefronts/livingroomCollective/LivingroomCollective.jpg"
```

---

### `photoLabelLeft` / `photoLabelRight`
Text labels overlaid on the lower-right corner of each half of a side-by-side combined photo. Only useful when the photo is a two-panel image.
```yaml
photoLabelLeft: "Toni Brou"
photoLabelRight: "Brandt Minden"
```

---

### `blurb`
A short description of the storefront, displayed below the photo. Accepts HTML.
```yaml
blurb: "Imagine a warm and inviting living room space. Come hang out and purchase art!"
```

---

### `artists`
List of artists. Each artist has the following fields:

#### `name` *(required)*
```yaml
name: "Kim Brook"
```

#### `image`
Path to the artist's photo, relative to `static/`. Displays as a square on desktop, 16:9 cropped from the top on mobile.
```yaml
image: "/images/storefronts/livingroomCollective/Kim.webp"
```

#### `bio`
Short artist biography. Accepts HTML (`<b>`, `<i>`, etc.).
```yaml
bio: "Kim is a Visual Artist, Arts Educator, and Community Visionary."
```

#### `links`
List of links shown as icons (Instagram, Facebook) or emoji (Website, etc.).

| `label`     | Display         | Requires       |
|-------------|-----------------|----------------|
| `Instagram` | Instagram icon  | `url`          |
| `Facebook`  | Facebook icon   | `url`          |
| anything else | `emoji` field | `url`, `emoji` |

```yaml
links:
  - label: "Instagram"
    url: "https://www.instagram.com/kimbrookceramics/"
  - label: "Website"
    emoji: "🌐"
    url: "https://example.com"
```

---

## Full Example

```yaml
locationName: "Example Gallery"
address1: "123 Massachusetts St"
address2: "Lawrence, KS 66044"
hoursHeading: "Hours"
hours:
  - "Thursday–Friday: 11am to 7pm"
  - "Saturday–Sunday: 11am to 3pm"
events:
  - "Grand Opening: July 31, 5–9pm"
  - "Live Music: August 10, 7pm"
photo: "/images/storefronts/example/gallery.jpg"
photoLabelLeft: "Artist A"
photoLabelRight: "Artist B"
blurb: "A wonderful gallery in the heart of Lawrence."
artists:
  - name: "Jane Smith"
    image: "/images/storefronts/example/jane.jpg"
    bio: "Jane makes <i>beautiful</i> things."
    links:
      - label: "Instagram"
        url: "https://www.instagram.com/janesmith/"
      - label: "Website"
        emoji: "🌐"
        url: "https://janesmith.com"
```
