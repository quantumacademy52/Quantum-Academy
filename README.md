[README.md](https://github.com/user-attachments/files/34216442/README.md)
# Quantum-Academy

Homepage for **Quantum Academy**, a robotics, AI and STEM education academy in Karachi, Pakistan.

It is a single static page built with plain HTML, CSS and JavaScript. There is no build step, no framework and nothing to install.

## Features

- Hero slider with four slides, arrows, dots, swipe and autoplay. Any slide can use a background video or photo.
- Robot illustration that assembles itself on load, with eyes that follow the pointer.
- Scrolling ticker of partner schools.
- Sections for why schools choose Quantum Academy, learning by building, core services, about, recognition, schools and partners, testimonials, news coverage, Instagram, a video and photo slider, and contact.
- Pinned Instagram badge with profile picture and handle, plus a WhatsApp chat button.
- Instagram preview and Google Map that open the real app when tapped, so a swipe never gets trapped inside an embed.
- Built for showing on phones in meetings: pinch-zoom and sideways dragging are locked so the layout cannot be pushed off screen.
- Respects the reduced-motion setting.

## Run it locally

Open `index.html` in a browser. An internet connection is needed for the font, logo, map and Instagram preview.

To use a local server instead:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploy with GitHub Pages

1. Put `index.html` in the root of the repository and push it to GitHub.
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then save.
4. After a minute or two the site is live at `https://<your-username>.github.io/<repository-name>/`.

## Editing the content

Everything is in `index.html`. Page text lives in the HTML. Media, testimonials, news coverage and school lists live in the script at the bottom of the file.

| Section | ID | Where to edit |
| --- | --- | --- |
| Hero, slide 1 | `#top` | HTML (headline, summary, robot, facts row) |
| Hero, slides 2 to 4 | `#top` | `SLIDES` in the script |
| School ticker | | Built from the `P` and `O` school lists |
| Why schools choose | `#why` | HTML |
| Learning by building | `#learn` | HTML |
| Core services | `#services` | HTML |
| About, vision and mission | `#about` | HTML |
| Recognition and leader | `#record` | HTML |
| Schools and partners | `#schools` | `P` and `O` in the script |
| Testimonials | `#testimonials` | `QUOTES` in the script |
| In the news | `#news` | `PRESS` in the script |
| Instagram | `#instagram` | HTML |
| See us in action | `#watch` | `MEDIA` in the script |
| Contact and map | `#contact` | HTML |

### Adding media, quotes and news coverage

Find the media config block in the script and fill in the lists:

```js
const SLIDES = [
  { h: 'Headline', p: 'Supporting text.', chips: ['Point one', 'Point two', 'Point three'],
    cta: ['Button label', '#contact'], video: 'https://example.com/clip.mp4', img: 'https://example.com/poster.jpg' }
];
const MEDIA  = [{ title: 'Robotics day', video: 'https://example.com/clip.mp4', poster: 'https://example.com/poster.jpg' }];
const QUOTES = [{ q: 'Quote text', n: 'Name', r: 'Parent, Karachi' }];
const PRESS  = [
  { name: 'Channel or paper', logo: 'https://example.com/logo.png', href: 'https://example.com/article' },
  { name: 'Aaj News', title: 'Video title', youtube: 'To7g_MVUhlE', href: 'https://youtu.be/To7g_MVUhlE' }
];
const SAMPLES = false;
```

- In `SLIDES`, `video` and `img` are optional. Use short, muted `.mp4` loops for slide backgrounds.
- In `PRESS`, an entry with `youtube` (the video ID from the link) becomes a featured video with a play button. Entries without it become logo tiles.
- `SAMPLES` is `true` by default. While it is `true`, empty sections show tiles marked **Sample** so the layout can be reviewed. **Set it to `false` before going live.** With it off, a section with no content stays hidden.

### School lists

`P` is the institutional partnerships list and `O` is the other schools list. Each entry is:

```js
['School name', 'Optional note', [['Link label', 'Google place ID or full URL']]]
```

### Other common edits

- **Contact details:** the contact section and the footer. The WhatsApp button uses `https://wa.me/<country code and number>` with no plus sign or spaces.
- **Instagram handle:** appears in the nav icon, pinned badge, Instagram section, contact section and footer. Use find and replace to change it everywhere.
- **Logo:** loaded from Cloudinary by the `L` function in the script.
- **Instagram badge picture:** set by the `AV` constant in the script. It uses the logo by default.
- **Colours:** CSS variables at the top of the `<style>` block (`--blue`, `--yellow`, `--deep`, `--sky`).

## Mobile and accessibility notes

- Zoom is locked on purpose because the site is shown to school owners on phones. To allow zoom again, remove `maximum-scale=1,user-scalable=no` from the viewport meta tag, the `touch-action` rules in the CSS and the `gesturestart` listener at the end of the script.
- Animations and slider autoplay are switched off for visitors who prefer reduced motion.
- Inactive slides are removed from keyboard focus and screen readers.

## Content guidelines

Only publish facts the academy has confirmed: dates, schools served, certificates and results. Do not add press coverage, testimonials, awards or competition results unless they are real and approved by the academy.

## Built with

- HTML, CSS and vanilla JavaScript
- [Bricolage Grotesque](https://fonts.google.com/specimen/Bricolage+Grotesque) from Google Fonts
- Cloudinary for the logo
- Google Maps embed and link
- Instagram profile embed
- WhatsApp click-to-chat link

Works in current versions of Chrome, Edge, Firefox and Safari (iOS 16 or newer recommended).

## License

All rights reserved. The Quantum Academy name, logo and content belong to Quantum Academy. Add a `LICENSE` file if you want to allow others to reuse the code.
