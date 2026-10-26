---
title: ZeroSyl Output Examples in Praat
---

<style>
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
</style>

# ZeroSyl Output Examples in Praat

Your Name, Stellenbosch University

[[report](#)]

This page accompanies my report *Your Report Title*. Each video shows ZeroSyl's
syllable segmentation next to the ground-truth (GT) TextGrid in
[Praat](https://www.fon.hum.uva.nl/praat/), for utterance ID 82. The video titles
give the interval between the two boundaries being examined (for example,
"post 48to49").

<div id="videos"></div>

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

  let n = 0;
  let html = '<p><strong>Contents</strong></p><ol>' +
    sections.map(s => '<li><a href="#' + s.id + '">' + s.title + '</a></li>').join('') + '</ol>';

  sections.forEach((s, i) => {
    html += '<h2 id="' + s.id + '">' + (i + 1) + '. ' + s.title + '</h2>';
    s.videos.forEach(v => {
      n++;
      const name = "ID " + UTTERANCE_ID + ", post " + v.post;
      html += '<div id="video-' + n + '" class="video-wrap">' +
        '<iframe loading="lazy" src="https://www.youtube-nocookie.com/embed/' + v.yt + '" ' +
        'title="' + name + '" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>' +
        '</div><p class="caption">Video ' + n + ' (' + name + '): ' + v.caption + '</p>';
    });
  });
  document.getElementById("videos").innerHTML = html;

  // Jump to a section or video from the URL, e.g. .../#gt-errors or .../#video-5
  function openFromHash() {
    const el = location.hash && document.getElementById(location.hash.slice(1));
    if (el) el.scrollIntoView();
  }
  window.addEventListener("hashchange", openFromHash);
  openFromHash();
</script>

<noscript>This page needs JavaScript turned on to show the videos.</noscript>
