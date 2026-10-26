---
title: ZeroSyl Output Examples in Praat
---

<style>
  .tabs {
    display: flex;
    gap: 0.5em;
    border-bottom: 2px solid #ddd;
    margin: 1.5em 0 2em 0;
  }
  .tab {
    font: inherit;
    font-size: 1em;
    padding: 0.6em 1.2em;
    border: 1px solid #ddd;
    border-bottom: none;
    border-radius: 6px 6px 0 0;
    background: #f5f5f5;
    color: #333;
    cursor: pointer;
    margin-bottom: -2px;
  }
  .tab[aria-selected="true"] {
    background: #fff;
    border-bottom: 2px solid #fff;
    font-weight: bold;
  }
  .view[hidden] { display: none; }
  .video-wrap {
    position: relative;
    width: 100%;
    max-width: 800px;
    aspect-ratio: 16 / 9;
    margin: 0 auto 0.5em auto;
  }
  .video-wrap iframe {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    border: 0;
  }
  .caption {
    text-align: center;
    font-size: 0.9em;
    color: #555;
    margin-bottom: 2.5em;
  }
  .tag {
    display: inline-block;
    font-size: 0.85em;
    background: #eef3f8;
    border-radius: 4px;
    padding: 0.1em 0.5em;
    margin-left: 0.3em;
  }
</style>

# ZeroSyl Output Examples in Praat

Your Name, Stellenbosch University

[[report](#)]

This page accompanies my report *Your Report Title*. Each video shows ZeroSyl's
syllable segmentation next to the ground-truth (GT) TextGrid in
[Praat](https://www.fon.hum.uva.nl/praat/), for utterance ID 82. The video titles
give the interval between the two boundaries being examined (for example,
"post 48to49"). Video numbers are the same in both tabs.

<div class="tabs" role="tablist">
  <button class="tab" role="tab" data-tab="type" aria-selected="true">By error type</button>
  <button class="tab" role="tab" data-tab="alpha" aria-selected="false">All videos (A–Z)</button>
</div>

<div id="view-type" class="view" role="tabpanel"></div>
<div id="view-alpha" class="view" role="tabpanel" hidden></div>

<script>
  // ---- Edit this list to add or change videos ----
  // Each section is one error type. Videos are numbered in this order.
  const sections = [
    { id: "boundary-tolerance", title: "Boundary outside the 50 ms tolerance", videos: [
      { yt: "rLTYmoAygH4", post: "48to49", caption: "ZeroSyl places the boundary outside the 50 ms tolerance." }
    ]},
    { id: "oversegmentation", title: "Over-segmentation", videos: [
      { yt: "QLWD2xWso8Y", post: "2to3",   caption: "ZeroSyl over-segments, placing extra boundaries." },
      { yt: "l7sbA6UgYXQ", post: "50to52", caption: "ZeroSyl over-segments, placing extra boundaries." }
    ]},
    { id: "undersegmentation", title: "Under-segmentation", videos: [
      { yt: "5f9Teqe0RWk", post: "18to20", caption: "ZeroSyl under-segments, missing boundaries." },
      { yt: "U1yTGIyaqcM", post: "22to23", caption: "ZeroSyl under-segments, missing boundaries." }
    ]},
    { id: "word-as-silence", title: "Word mistaken for silence", videos: [
      { yt: "nNdqnpf-lEQ", post: "24to25", caption: "ZeroSyl mistakes a word for silence." }
    ]},
    { id: "noise-as-syllable", title: "Background noise mistaken for a syllable", videos: [
      { yt: "BD-QsLhwx0w", post: "35to36", caption: "ZeroSyl mistakes background noise for a syllable." },
      { yt: "zzwSPC0Cx6o", post: "32to33", caption: "ZeroSyl mistakes background noise for a syllable." }
    ]},
    { id: "gt-silence", title: "Silence in the GT, none in ZeroSyl", videos: [
      { yt: "DVOqCvNhNQ8", post: "46to47", caption: "The ground truth marks a silence, but ZeroSyl does not." }
    ]},
    { id: "noise-clouds-judgement", title: "Background noise clouds ZeroSyl's judgement", videos: [
      { yt: "6ZJ6_jdzq3s", post: "36to37", caption: "Background noise clouds ZeroSyl's judgement." }
    ]},
    { id: "gt-errors", title: "Errors in the ground truth", videos: [
      { yt: "ZYvNs5F-2a4", post: "45to46", caption: "An error in the ground truth." },
      { yt: "euPz_4IUwNk", post: "39to40", caption: "An error in the ground truth." }
    ]},
    { id: "disputable", title: "Disputable cases", videos: [
      { yt: "elwTd4Shw0U", post: "33to34", caption: "It is disputable whether ZeroSyl or the ground truth is right." },
      { yt: "feqRRU25gD0", post: "29to30", caption: "It is disputable whether ZeroSyl or the ground truth is right." }
    ]}
  ];
  const UTTERANCE_ID = "82";
  // ---- End of list ----

  const all = [];
  let n = 0;
  sections.forEach((s, i) => {
    s.number = i + 1;
    s.videos.forEach(v => {
      v.n = ++n;
      v.name = "ID " + UTTERANCE_ID + ", post " + v.post;
      v.section = s;
      all.push(v);
    });
  });

  function videoHTML(v, anchorPrefix, showTag) {
    const tag = showTag ? '<br><span class="tag">' + v.section.title + '</span>' : '';
    return '<div id="' + anchorPrefix + v.n + '" class="video-wrap">' +
      '<iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/' + v.yt + '" ' +
      'title="' + v.name + '" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>' +
      '</div><p class="caption">Video ' + v.n + ' (' + v.name + '): ' + v.caption + tag + '</p>';
  }

  // Tab 1: by error type
  let typeHTML = '<p><strong>Contents</strong></p><ol>' +
    sections.map(s => '<li><a href="#' + s.id + '">' + s.title + '</a></li>').join('') + '</ol>';
  sections.forEach(s => {
    typeHTML += '<h2 id="' + s.id + '">' + s.number + '. ' + s.title + '</h2>';
    s.videos.forEach(v => { typeHTML += videoHTML(v, "video-", false); });
  });
  document.getElementById("view-type").innerHTML = typeHTML;

  // Tab 2: all videos sorted by title (natural order, so "post 2to3" comes before "post 18to20")
  const sorted = all.slice().sort((a, b) =>
    a.name.localeCompare(b.name, undefined, { numeric: true, sensitivity: "base" }));
  document.getElementById("view-alpha").innerHTML = sorted.map(v => videoHTML(v, "az-video-", true)).join('');

  // Tab switching
  const tabs = document.querySelectorAll(".tab");
  function showTab(name) {
    tabs.forEach(t => t.setAttribute("aria-selected", t.dataset.tab === name ? "true" : "false"));
    document.getElementById("view-type").hidden = name !== "type";
    document.getElementById("view-alpha").hidden = name !== "alpha";
  }
  tabs.forEach(t => t.addEventListener("click", () => {
    showTab(t.dataset.tab);
    history.replaceState(null, "", t.dataset.tab === "alpha" ? "#all-videos" : "#by-type");
  }));

  // Open the right tab from the URL, e.g. .../#all-videos or .../#gt-errors or .../#video-5
  function openFromHash() {
    const h = location.hash.slice(1);
    if (h === "all-videos" || h.startsWith("az-video-")) showTab("alpha");
    else showTab("type");
    const el = h && document.getElementById(h);
    if (el) el.scrollIntoView();
  }
  window.addEventListener("hashchange", openFromHash);
  openFromHash();
</script>

<noscript>This page needs JavaScript turned on to show the videos.</noscript>
