---
layout: post
title: A Minimalist MIDI Synth with Sine Waves
description: Tutorial on how to implement a MIDI software synthesizer in Python by using sine waves.
---

Let's implement a minimalist MIDI software synthesizer by using sine waves!

<p>
  <b>Sample output:</b><br>
  <audio controls>
    <source src="{{ '/assets/midi-synth/demo.ogg' | relative_url }}" type="audio/mpeg">
    Your browser does not support the audio element.
  </audio>
</p>

## About MIDI Synthesis

[Software synthesizers][1]{:target="_blank"} convert MIDI data into audio signals to be either played through an audio device or stored to a file.

### MIDI Data Examples

* **Note On Event**: a note starts playing with a given velocity at a given time.
* **Note Off Event**: a note stops playing at a given time.

Based on MIDI data, software synthesizers implement techniques in order to emulate the sound of real instruments.

## A Minimal MIDI Synthesizer

Our synth aims at being as simple and fun to implement as possible.

Basically, for each playing note in the MIDI file we compute the corresponding sine wave and add it to the final waveform we'll listen to.

### _Step 1: MIDI Data Collection_

We collect the following MIDI data for each note to be played.

* **_note_**, which is the MIDI note number;
* **_velocity_**, which says how hard the note is played (from 0 to 127);
* **_start-_** and **_end-time_**, which say when the note starts and stops playing (in seconds).

Let _S_ denote the <u>total number of seconds</u> of the MIDI tune (i.e. the maximum _end-time_).

### _Step 2: Waveform Initialization + Time Array_

We zero-initialize the <u>waveform array</u> _W_ of length &#8968;44100&times;_S_&#8969; that we'll populate with the amplitude values (i.e. the samples) of the final waveform.

Namely, _W_ will contain a number of 44100 samples for each second in the MIDI tune. (Notice that 44100 is a standard sampling rate for audio.)

We also create the <u>time array</u> _T_ related to _W_ by computing all the &#8968;44100&times;_S_&#8969; equidistant units of time (i.e. time steps) from 0 to _S_, namely

* The _i_-th time step _T_[_i_] is the time of the _i_-th sample _W_[_i_]; in other words
* The _i_-th sample _W_[_i_] stores the amplitude of the final waveform _W_ at time _t_ = _T_[_i_].

### _Step 3: Sine Waves Computation + [Additive Synthesis][2]{:target="_blank"}_

For each collected tuple (_note_, _velocity_, _start-time_, _end-time_) we compute the corresponding sine wave and add it to _W_:

1. Get the frequency _f_ associated to the _note_;
2. Compute the amplitude _A_ = _velocity_ &divide; 127, i.e. normalize the _velocity_ to a 0-1 range;
3. Let _s_ and _e_ denote _start-_ and _end-time_, respectively;
4. Compute the sine wave _A_ &middot; sin(2&pi; &middot; _f_ &middot; _t_), for each _t_ such that _s_ &le; _t_ &le; _e_.
5. Add the sine wave to the waveform array _W_.

Summing up, we add the computed sine wave to _W_ at the corresponding _t_-values as follows:

* For each _i_ from &#8970;44100&times;_s_&#8971; to &#8970;44100&times;_e_&#8971;, do
	* _t_ = _T_[_i_];
	* _W_[_i_] = _W_[_i_] + _A_ &middot; sin(2&pi; &middot; _f_ &middot; _t_).

_**To understand Step 3 better, read:**_

* ["_Note names, MIDI numbers and frequencies_"][3]{:target="_blank"} by Joe Wolfe, on how to compute a note frequency w.r.t. its distance to the note A4 (440 Hz), namely _f_ = 2<sup>(note distance from A4)&divide;12</sup> &times; 440;
* ["_Sinusoidal Waves as Sound_"][4]{:target="_blank"} by Jonathan Rogness, on how to play multiple notes by adding their sine waves together, which includes nice plots and examples.


### _Final Step: Waveform Playback_

By default we automatically play the computed waveform _W_ through the speakers. On user request, we store it on a specified WAV file without playing it.

## The Implementation

[_**See the example and get the code!**_][5]{:title="GitHub Repository"}

This work was initially inspired by Robert Elder's article [_"Compose Music From Entropy in /dev/urandom"_][6]{:target="_blank"}.

[1]: https://en.wikipedia.org/wiki/Software_synthesizer
[2]: https://en.wikipedia.org/wiki/Additive_synthesis
[3]: https://newt.phys.unsw.edu.au/jw/notes.html
[4]: https://www-users.cse.umn.edu/~rogness/math1155/soundwaves/
[5]: https://github.com/massimo-nazaria/midi-synth
[6]: https://blog.robertelder.org/bash-one-liner-compose-music/