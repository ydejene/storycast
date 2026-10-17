# StoryCast

StoryCast is a three-page accessible microsite that showcases audio and video storytelling in a semantically structured, research-informed design. It emphasizes accessibility, semantic HTML, Sass, and user-centered design practices. The site pairs a concise introduction to the project with an explainer about schizophrenia, using an editorial visual style and multiple ways to access the narrated story. The schizophrenia page is general education, not a personal testimony or individual medical guidance.

## Pages

- **Home** (`index.html`): introduces StoryCast, features the schizophrenia explainer, and previews future topics.
- **About** (`about.html`): describes the project's editorial approach, accessibility formats, and external public-health resources.
- **Understanding Schizophrenia** (`story/understanding-schizophrenia.html`): presents the educational article, narrated video, optional captions, audio alternative, expandable transcript, and source links.

## Project Structure

```text
storycast/
|-- index.html
|-- about.html
|-- story/
|   `-- understanding-schizophrenia.html
|-- sass/
|   |-- main.scss
|   |-- _tokens.scss
|   |-- _reset.scss
|   |-- _layout.scss
|   |-- _typography.scss
|   |-- _nav.scss
|   |-- _footer.scss
|   |-- _components.scss
|   |-- _home.scss
|   |-- _story.scss
|   |-- _about.scss
|   `-- _responsive.scss
|-- css/main.css
|-- assets/
|   |-- images/favicon.ico
|   |-- video/StoryCastSchizoPhreniaVideo.mp4
|   |-- audio/StoryCastSchizophrenia.m4a
|   `-- captions/caption.vtt
|-- LICENSE
|-- package.json
`-- package-lock.json
```

The narration source is maintained in `week_7/transcription.md` in the parent workspace and is not part of this repository. The compiled stylesheet is generated from `sass/main.scss` and its partials.

## Technologies

- Semantic HTML5
- Sass (Dart Sass) with partials and CSS custom-property tokens for color, typography, and spacing
- CSS Grid, Flexbox, viewport media queries, and a container query that adjusts topic-card spacing and heading size to the card's available width
- Native HTML video, audio, WebVTT captions, and disclosure controls

The homepage photography is served from the existing Unsplash image URLs. The Google Fonts import in the Sass tokens also requires an internet connection; local system font fallbacks are configured.

## Install and Run

### Video setup

The story video is stored with Git LFS. Install Git LFS before cloning, then initialize it once for your user account:

```sh
git lfs install
```

A normal clone will then retrieve the video along with the repository. If the repository was cloned before Git LFS was installed, download its LFS files with:

```sh
git lfs pull
```

### Run locally

From this directory:

```sh
npm install
npm run sass:build
python -m http.server 3400
```

Open `http://localhost:3400/`. The Python server uses the project directory as its document root. In VS Code, open this repository folder and use Live Server on `index.html`; project links are relative to their HTML documents so they also resolve under the repository's nested URL path.

The build compiles `sass/main.scss` to `css/main.css`, replacing the generated stylesheet. To recompile automatically while editing Sass, run `npm run sass:watch`.

## Accessibility Checklist

- [x] Each page uses a document language, a page-level `<header>`, `<nav>`, `<main>`, and `<footer>` landmarks, plus a skip link to main content.
- [x] Page content uses headings, sections, and articles to express its hierarchy. The story's in-page section links are grouped in a labeled navigation landmark.
- [x] Primary navigation identifies the current page with `aria-current="page"`; links and media controls have visible text or accessible names.
- [x] Keyboard focus is visibly outlined for links and the transcript disclosure. Video, audio, and `<details>/<summary>` use native browser controls.
- [x] Decorative SVGs are hidden from assistive technology; homepage images have descriptive alternative text.
- [x] The story media is described with a `<figure>` and visible `<figcaption>`. The video has a descriptive accessible name.
- [x] The video includes an English WebVTT caption track. Captions are also burned into the video; the WebVTT track is optional and is not set as default to avoid duplicate captions.
- [x] An audio-only alternative and a readable, expandable transcript are provided for the narration.
- [x] Reduced-motion preferences are respected for smooth scrolling and transitions.
- [x] Responsive layouts use CSS Grid, Flexbox, viewport breakpoints, and a container query for the topic cards.
- [x] WCAG 2.1 AA conformance and color-contrast ratios verified.

## Media and Transcript

The story page uses the local MP4 video, M4A audio alternative, and `assets/captions/caption.vtt`. The WebVTT track is an optional player caption selection because the video already has burned-in captions. The written narration appears in an expandable transcript on the story page and is maintained from the workspace source `week_7/transcription.md`. Keep these formats together when updating narration so their wording remains aligned.

## Planning and Research

The project research document is available at the repository root:

[StoryCastResearchDocument.pdf](StoryCastResearchDocument.pdf)
