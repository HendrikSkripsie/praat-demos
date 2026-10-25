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

Hendrik de Man, Stellenbosch University

[[report](#)]

This page accompanies my report Syllable counting and diarisation of child
audio using machine learning. Each video shows ZeroSyl's
syllable segmentation next to the ground-truth (GT) TextGrid in
[Praat](https://www.fon.hum.uva.nl/praat/), for utterance ID 82. The video titles
give the interval between the two boundaries being examined (for example,
"post 48to49").

**Contents**

1. [Boundary outside the 50 ms tolerance](#1-boundary-outside-the-50-ms-tolerance)
2. [Word mistaken for silence](#2-word-mistaken-for-silence)
3. [Background noise mistaken for a syllable](#3-background-noise-mistaken-for-a-syllable)
4. [Silence in the GT, none in ZeroSyl](#4-silence-in-the-gt-none-in-zerosyl)
5. [Background noise clouds ZeroSyl's judgement](#5-background-noise-clouds-zerosyls-judgement)
6. [Errors in the ground truth](#6-errors-in-the-ground-truth)
7. [Disputable cases](#7-disputable-cases)

## 1. Boundary outside the 50 ms tolerance

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/rLTYmoAygH4"
          title="ID 82, post 48to49"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 1 (ID 82, post 48to49): ZeroSyl places the boundary outside the 50 ms tolerance.</p>

## 2. Word mistaken for silence

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/nNdqnpf-lEQ"
          title="ID 82, post 24to25"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 2 (ID 82, post 24to25): ZeroSyl mistakes a word for silence.</p>

## 3. Background noise mistaken for a syllable

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/BD-QsLhwx0w"
          title="ID 82, post 35to36"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 3 (ID 82, post 35to36): ZeroSyl mistakes background noise for a syllable.</p>

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/zzwSPC0Cx6o"
          title="ID 82, post 32to33"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 4 (ID 82, post 32to33): ZeroSyl mistakes background noise for a syllable.</p>

## 4. Silence in the GT, none in ZeroSyl

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/DVOqCvNhNQ8"
          title="ID 82, post 46to47"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 5 (ID 82, post 46to47): The ground truth marks a silence, but ZeroSyl does not.</p>

## 5. Background noise clouds ZeroSyl's judgement

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/6ZJ6_jdzq3s"
          title="ID 82, post 36to37"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 6 (ID 82, post 36to37): Background noise clouds ZeroSyl's judgement.</p>

## 6. Errors in the ground truth

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/ZYvNs5F-2a4"
          title="ID 82, post 45to46"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 7 (ID 82, post 45to46): An error in the ground truth.</p>

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/euPz_4IUwNk"
          title="ID 82, post 39to40"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 8 (ID 82, post 39to40): An error in the ground truth.</p>

## 7. Disputable cases

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/elwTd4Shw0U"
          title="ID 82, post 33to34"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 9 (ID 82, post 33to34): It is disputable whether ZeroSyl or the ground truth is right.</p>

<div class="video-wrap">
  <iframe src="https://www.youtube-nocookie.com/embed/feqRRU25gD0"
          title="ID 82, post 29to30"
          allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen></iframe>
</div>
<p class="caption">Video 10 (ID 82, post 29to30): It is disputable whether ZeroSyl or the ground truth is right.</p>
