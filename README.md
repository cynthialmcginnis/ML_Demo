# ARIN 310 — Interactive Machine Learning Demos

Four browser-based, hands-on tools built for **ARIN 310: Introduction to Artificial Intelligence** (Unit 2 — Machine Learning and Deep Learning). Each demo exposes the actual mechanism behind a technique — the loss being minimized, the search for a better answer, the moments where the algorithm gets it wrong — instead of producing a black-box result.

**Live site:** `https://cynthialmcginnis.github.io/ML_Demo/`

No build step, no dependencies, no backend. Every demo is a single self-contained HTML file (inline CSS and JavaScript) that runs entirely in the browser.

## Demos

| Demo | Concept | File |
|---|---|---|
| Finding the Line That Fits | Supervised learning — linear regression, one feature | `linear-regression-demo.html` |
| When One Line Isn't Enough | Supervised learning — multiple features, 3D plane fitting | `multi-feature-regression-demo.html` |
| Finding Structure Without Labels | Unsupervised learning — k-means clustering | `unsupervised-clustering-demo.html` |
| Real Tweets, Real Ambiguity | Semi-supervised learning — label propagation on real data | `disaster-tweets-label-propagation-demo.html` |

`index.html` is the landing page linking all four.

### 1. Finding the Line That Fits
Students manually adjust slope and intercept to fit a line through a study-hours-vs-exam-score dataset, watching Sum of Squared Error update live via residual lines. A "Reveal Best-Fit Line" button animates to the least-squares solution and compares it to the student's manual attempt. Includes a "Make a Prediction" panel.

### 2. When One Line Isn't Enough
The two-feature follow-on: predicting home price from square footage and age. Since a plane can't be drawn on paper the way a line can, this demo renders an actual rotatable 3D scene (hand-rolled canvas projection, no external library) showing the fitted plane tilt in real time as its three weights change.

### 3. Finding Structure Without Labels
K-means clustering on unlabeled customer data (spending vs. visit frequency). Students place centroids by hand, then let Lloyd's algorithm iterate to convergence. Deliberately surfaces a real limitation: different starting centroids can converge to different, equally "valid" groupings.

### 4. Real Tweets, Real Ambiguity
Semi-supervised label propagation on real tweets from Kaggle's [*NLP with Disaster Tweets*](https://www.kaggle.com/competitions/nlp-getting-started) competition. Four hand-labeled seed tweets (two disaster, two casual) spread labels outward by nearest-neighbor distance. Deliberately includes real tweets that use disaster vocabulary figuratively ("I forgot to bring chocolate with me. Major disaster.") to demonstrate a genuine, well-documented failure mode: naive word-count features can't distinguish a real report from a figure of speech, and propagation can confidently mislabel as a result.

**Data note:** 26 tweets were selected from the competition's `train.csv`, screened for profanity, slurs, and political content, and used verbatim except for trimming a handful of trailing question-mark artifacts left over from emoji lost in CSV export. See the in-page source note for full attribution.

## Design notes

- Shared visual language across all four: warm paper background, serif display headings, monospace numerals, a consistent "reveal the best answer and compare it to your guess" interaction pattern.
- No frameworks, no build tools, no CDN dependencies — everything works offline once the file is downloaded.
- Respects `prefers-reduced-motion` throughout.
- Each demo includes a "Make a Prediction" panel that runs a new input through the current model and shows its work (matched example, distance, confidence) rather than returning a bare answer.

## Updating a demo

Each HTML file is fully self-contained — open it in any text editor, make changes, and re-upload to replace it. No rebuild step required.

## License / reuse

Built for classroom use in ARIN 310, Section A301, Fall 2026. Tweet data is subject to Kaggle's competition terms; see the source note inside `disaster-tweets-label-propagation-demo.html` for details.
