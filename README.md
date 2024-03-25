# MAGI
MAGI: Multimodal Audio and Gesture, Integrated

Although humans engaged in face-to-face conversation simultaneously communicate both verbally and non-verbally, methods for joint and unified synthesis of speech audio and co-speech 3D gesture motion from text are a new and emerging field. These technologies hold great promise for more human-like, efficient, expressive, and robust synthetic communication, but are currently held back by the lack of suitably large datasets, as existing methods are trained on parallel data from all constituent modalities. Inspired by student-teacher methods, we propose a straightforward solution to the data shortage, by simply synthesising additional training material. Specifically, we use unimodal synthesis models trained on large datasets to create multimodal (but synthetic) parallel training data, and then pre-train a joint synthesis model on that material. In addition, we propose a new synthesis architecture that adds better and more controllable prosody modelling to the state-of-the-art method in the field. Our results confirm that pre-training on large amounts of synthetic data improves the quality of both the speech and the motion synthesised by the multimodal model, with the proposed architecture yielding further benefits when pre-trained on the synthetic data.



<style type="text/css">
    .tg {
    border-collapse: collapse;
    border-color: #9ABAD9;
    border-spacing: 0;
  }

  .tg td {
    background-color: #EBF5FF;
    border-color: #9ABAD9;
    border-style: solid;
    border-width: 1px;
    color: #444;
    font-family: Arial, sans-serif;
    font-size: 14px;
    overflow: hidden;
    padding: 0px 20px;
    word-break: normal;
    font-weight: bold;
    vertical-align: middle;
    horizontal-align: center;
    white-space: nowrap;
  }

  .tg th {
    background-color: #000000;
    border-color: #9ABAD9;
    border-style: solid;
    border-width: 1px;
    color: #fff;
    font-family: Arial, sans-serif;
    font-size: 14px;
    font-weight: normal;
    overflow: hidden;
    padding: 0px 20px;
    word-break: normal;
    font-weight: bold;
    vertical-align: middle;
    horizontal-align: center;
    white-space: nowrap;
    padding: 10px;
    margin: auto;
  }

  .tg .tg-0pky {
    border-color: inherit;
    text-align: center;
    vertical-align: top,
  }

  .tg .tg-fymr {
    border-color: inherit;
    font-weight: bold;
    text-align: center;
    vertical-align: top
  }
  .slider {
  -webkit-appearance: none;
  width: 75%;
  height: 15px;
  border-radius: 5px;
  background: #d3d3d3;
  outline: none;
  opacity: 0.7;
  -webkit-transition: .2s;
  transition: opacity .2s;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #409cff;
  cursor: pointer;
}

.slider::-moz-range-thumb {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background: #409cff;
  cursor: pointer;
}

audio {
    width: 240px;
}

/* CSS */
.button-12 {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 6px 14px;
  font-family: -apple-system, BlinkMacSystemFont, 'Roboto', sans-serif;
  border-radius: 6px;
  border: none;

  background: #6E6D70;
  box-shadow: 0px 0.5px 1px rgba(0, 0, 0, 0.1), inset 0px 0.5px 0.5px rgba(255, 255, 255, 0.5), 0px 0px 0px 0.5px rgba(0, 0, 0, 0.12);
  color: #DFDEDF;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-12:focus {
  box-shadow: inset 0px 0.8px 0px -0.25px rgba(255, 255, 255, 0.2), 0px 0.5px 1px rgba(0, 0, 0, 0.1), 0px 0px 0px 3.5px rgba(58, 108, 217, 0.5);
  outline: 0;
}

video {
  margin: 1em;
}

</style>


<script>

  transcript_audio_only = {
    1: "Like every, I think most people even people who never go to mass ever will go to mass on Christmas Eve or Christmas Day. So like what we used to do is we used to go to mass on Christmas Eve which was lovely it's such a nice ceremony because it's so like it's obviously 12 o'clock at night.",
    2: "Eventually got to a point where I was like okay I need to stop doing this sort of stuff Like it just doesn't make any sense as to why because I was getting hurt like there was times where like, I was like tearing muscles and I never broke a bone which I'm pretty proud of.",
    3: "But I remember once my parents were just downstairs in the kitchen and this is when mobile phones just began coming out. So, like my oldest brother and my oldest sister had a mobile phone each I'm pretty sure.",
    4: "But and again so that doesn't help people like myself and my friend who actually want to strike up a conversation with a genuine person out in the open because we don't want to go online. We don't feel like we have to do that."
  }

  function play_audio(filename, audio_id,  condition_name, transcription){

      audio = document.getElementById(audio_id);
      audio_source = document.getElementById(audio_id + "-src");
      block_quote = document.getElementById(audio_id + "-transcript");
      stimulus_span = document.getElementById(audio_id + "-span");

      audio.pause();
      audio_source.src = filename;
      block_quote.innerHTML = transcription;
      stimulus_span.innerHTML = condition_name;
      audio.load();
      audio.play();
  }

</script>

## Example stimuli from the evaluation

### Speech-only evaluation

> Click the buttons in the table to load and play the different stimuli.

Currently loaded stimulus: <span id="audio-stimuli-from-listening-test-span" style="font-weight: bold;"> MAGI-FT , Sentence 1</span>

<p>Audio player: </p>
  <audio id="audio-stimuli-from-listening-test" controls>
    <source id="audio-stimuli-from-listening-test-src" src="stimuli/audio-only/MAGI-FT_1" type="audio/wav">
  </audio>

<p> Transcription: </p>
<blockquote style="height: 100px">
  <p id="audio-stimuli-from-listening-test-transcript">
    Like every, I think most people even people who never go to mass ever will go to mass on Christmas Eve or Christmas Day. So like what we used to do is we used to go to mass on Christmas Eve which was lovely it's such a nice ceremony because it's so like it's obviously 12 o'clock at night.
  </p>
</blockquote>

<table class="tg">
  <thead>
    <tr>
      <th class="tg-0pky">Text prompt #</th>
      <th class="tg-0pky">NAT</th>
      <th class="tg-0pky" colspan="2">MAT</th>
      <th class="tg-0pky" colspan="2">MA</th>
    </tr>
    <tr>
      <th class="tg-0pky"></th>
      <th class="tg-0pky"></th>
      <th class="tg-0pky">MAT-T</th>
      <th class="tg-0pky">MAT-FT</th>
      <th class="tg-0pky">MAGI-T</th>
      <th class="tg-0pky">MAGI-FT</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>1</td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/NAT_1.wav', 'audio-stimuli-from-listening-test', 'NAT , Sentence 1', transcript_audio_only[1])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-T_1.wav', 'audio-stimuli-from-listening-test', 'MAT-T , Sentence 1', transcript_audio_only[1])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-FT_1.wav', 'audio-stimuli-from-listening-test', 'MAT-FT , Sentence 1', transcript_audio_only[1])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-T_1.wav', 'audio-stimuli-from-listening-test', 'MAGI-T , Sentence 1', transcript_audio_only[1])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-FT_1.wav', 'audio-stimuli-from-listening-test', 'MAGI-FT , Sentence 1', transcript_audio_only[1])"/>
        </td>
    </tr>
    <tr>
        <td>2</td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/NAT_2.wav', 'audio-stimuli-from-listening-test', 'NAT , Sentence 2', transcript_audio_only[2])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-T_2.wav', 'audio-stimuli-from-listening-test', 'MAT-T , Sentence 2', transcript_audio_only[2])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-FT_2.wav', 'audio-stimuli-from-listening-test', 'MAT-FT , Sentence 2', transcript_audio_only[2])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-T_2.wav', 'audio-stimuli-from-listening-test', 'MAGI-T , Sentence 2', transcript_audio_only[2])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-FT_2.wav', 'audio-stimuli-from-listening-test', 'MAGI-FT , Sentence 2', transcript_audio_only[2])"/>
        </td>
    </tr>
    <tr>
        <td>3</td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/NAT_3.wav', 'audio-stimuli-from-listening-test', 'NAT , Sentence 3', transcript_audio_only[3])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-T_3.wav', 'audio-stimuli-from-listening-test', 'MAT-T , Sentence 3', transcript_audio_only[3])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-FT_3.wav', 'audio-stimuli-from-listening-test', 'MAT-FT , Sentence 3', transcript_audio_only[3])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-T_3.wav', 'audio-stimuli-from-listening-test', 'MAGI-T , Sentence 3', transcript_audio_only[3])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-FT_3.wav', 'audio-stimuli-from-listening-test', 'MAGI-FT , Sentence 3', transcript_audio_only[3])"/>
        </td>
    </tr>
    <tr>
        <td>4</td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/NAT_4.wav', 'audio-stimuli-from-listening-test', 'NAT , Sentence 4', transcript_audio_only[4])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-T_4.wav', 'audio-stimuli-from-listening-test', 'MAT-T , Sentence 4', transcript_audio_only[4])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAT-FT_4.wav', 'audio-stimuli-from-listening-test', 'MAT-FT , Sentence 4', transcript_audio_only[4])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-T_4.wav', 'audio-stimuli-from-listening-test', 'MAGI-T , Sentence 4', transcript_audio_only[4])"/>
        </td>
        <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_audio('stimuli/audio-only/MAGI-FT_4.wav', 'audio-stimuli-from-listening-test', 'MAGI-FT , Sentence 4', transcript_audio_only[4])"/>
        </td>
    </tr>
  </tbody>
</table>

### Gesture-only evaluation (no audio)

<video id="gesture-only-video" class="video-js" controls width="640" height="360">
    <source id="gesture-only-video-source" src="stimuli/gesture-only/MAT_50_C4_3_eval_0092.mp4" type='video/mp4' />
</video>

Currently loaded: <span id="playing-gesture-only" style="font-weight: bold;" > MA-50 1</span>

<blockquote style="height: 100px">
  <p id="gesture-only-transcription">
      I mean it it's not that I'm against it it's just that I just don't have the time and I just sometimes I'm not bothered and that sort of stuff.
  </p>
</blockquote>

<p style="height: 10px">
    <span style="color: #ee4444; font-weight: bold" id="sm-50-trigger"> </span> 
</p>

<script>

 transcript_video_only = {
    "1": "Trying to see if if we can go back to the olden ways of just talking to people and actually engaging and communicating and seeing if can relationships form with just.",
    "2": "But then it was annoying because I paid because you have to pay the hospital fee of like a hundred quid for, for being seen and all the tests and stuff done and then a receipt was sent to my house.",
    "3": "Like every, I think most people even people who never go to mass ever will go to mass on Christmas Eve or Christmas Day. So like what we used to do is we used to go to mass on Christmas Eve which was lovely it's such a nice ceremony because it's so like it's obviously 12 o'clock at night.",
    "4": "When I was in primary school I used to have this ruler and I used to put it between desks and I used to push the tables together so the ruler would be between the two tables."
 }
 

  gesture_only_video = document.getElementById('gesture-only-video')
  gesture_only_video_source = document.getElementById('gesture-only-video-source')
  gesture_only_span_text =  document.getElementById('playing-gesture-only')
  gesture_only_transcript = document.getElementById('gesture-only-transcription')

  trigger_span = document.getElementById('sm-50-trigger')

  function play_video(filename, text){
      id = text[text.length - 1];

      gesture_only_video.pause();
      gesture_only_video_source.src = filename;
      gesture_only_span_text.innerHTML = text;
      gesture_only_transcript.innerHTML = transcript_video_only[id];
      gesture_only_video.load();
      gesture_only_video.play();

  }
</script>

<table class="tg">
  <thead>
    <tr>
      <th class="tg-0pky">Text prompt #</th>
      <th class="tg-0pky">NAT</th>
      <th class="tg-0pky" colspan="2">MAT</th>
      <th class="tg-0pky" colspan="2">MA</th>
    </tr>
    <tr>
      <th class="tg-0pky"></th>
      <th class="tg-0pky"></th>
      <th class="tg-0pky">MAT-T</th>
      <th class="tg-0pky">MAT-FT</th>
      <th class="tg-0pky">MAGI-T</th>
      <th class="tg-0pky">MAGI-FT</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
            <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/NAT_1.mp4', 'NAT 1')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-T_1.mp4', 'MAT-T 1')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-FT_1.mp4', 'MAT-FT 1')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-T_1.mp4', 'MAGI-T 1')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-FT_1', 'MAGI-FT 1')"/>
    </td>
    </tr>
        <tr>
      <td>2</td>
            <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/NAT_2.mp4', 'NAT 2')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-T_2.mp4', 'MAT-T 2')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-FT_2.mp4', 'MAT-FT 2')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-T_2.mp4', 'MAGI-T 2')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-FT_2.mp4', 'MAGI-FT 2')"/>
      </td>
    </tr>
    <tr>
      <td>3</td>
            <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/NAT_3.mp4', 'NAT 3')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-T_3.mp4', 'MAT-T 3')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-FT_3.mp4', 'MAT-FT 3')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-T_3.mp4', 'MAGI-T 3')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-FT_3.mp4', 'MAGI-FT 3')"/>
      </td>
    </tr>
    <tr>
      <td>4</td>
            <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/NAT_4.mp4', 'NAT 4')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-T_4.mp4', 'MAT-T 4')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAT-FT_4.mp4', 'MAT-FT 4')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-T_4.mp4', 'MAGI-T 4')"/>
      </td>
      <td>
          <img src="images/play_button_black.png" height=40 style="cursor: pointer;" onclick="play_video('stimuli/gesture-only/MAGI-FT_4.mp4', 'MAGI-FT 4')"/>
      </td>
    </tr>
  </tbody>
</table>

<!-- ### Speech-and-gesture evaluation

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Matched</th>
    <th class="tg-0pky">Mismatched</th>
  </tr>
</thead>
<tbody>
  <tr>
      <td> 
          <video id="speech-and-gesture-video-matched" class="video-js" controls width="500" height="282">
              <source id="speech-and-gesture-video-matched-source" src="stimuli/speech-and-gesture/MAT_50_C4_3_eval_0150_matched.mp4" type='video/mp4' />
          </video>
      </td>
      <td>
        <video id="speech-and-gesture-video-mismatched" class="video-js" controls width="500" height="282">
              <source id="speech-and-gesture-video-mismatched-source" src="stimuli/speech-and-gesture/MAT_50_C4_3_eval_0150_mismatched.mp4" type='video/mp4' />
          </video>
      </td>
  </tr>
</tbody>
</table>
<h6> *Note: Matched versus mismatched stimuli were not labelled in the study and presented in random order. </h6>

Currently loaded: <span id="playing-speech-and-gesture-span" style="font-weight: bold;" > MA-50 1</span>

<blockquote style="height: 100px">
  <p id="speech-and-gesture-transcription">
    Yeah and then obviously there, there's certain choirs that come down to the church. There's a woman called, I can't remember her name. But she has an incredible voice. Like an amazing voice.
  </p>
</blockquote>

<script>

  speech_and_gesture_video_matched = document.getElementById('speech-and-gesture-video-matched')
  speech_and_gesture_video_matched_source = document.getElementById('speech-and-gesture-video-matched-source')

  speech_ang_gesture_video_mismatched = document.getElementById('speech-and-gesture-video-mismatched')
  speech_and_gesture_video_mismatched_source = document.getElementById('speech-and-gesture-video-mismatched-source')

  speech_and_gesture_span_text =  document.getElementById('playing-speech-and-gesture-span')
  speech_and_gesture_transcript = document.getElementById('speech-and-gesture-transcription')


  transcript_speech_and_gesture = {
    '1' : "Yeah and then obviously there, there's certain choirs that come down to the church. There's a woman called, I can't remember her name. But she has an incredible voice. Like an amazing voice.",
    '2' : "When you think about it, that you do as a child, it's just absolutely ridiculous that makes no sense. But you can always justify it back then because it just seemed like the fun right thing to do.",
    '3' : "You walk around Dublin city centre and even if you try and strike up a conversation with somebody it's impossible because everyone has their headphones in. And again, I would listen to podcasts sometimes with my headphones in walking around the streets.",
    '4' : "Just so this whole social networking stuff just really really annoys me and cause it just warps people's minds and people are so Fixated on their phones and that sort of stuff that I just hate that so much."
  }


  function play_speech_and_gesture_eval(matched_filename, mismatched_filename, text){
      id = text[text.length - 1];

      speech_and_gesture_video_matched.pause();
      speech_ang_gesture_video_mismatched.pause();

      speech_and_gesture_video_matched_source.src = matched_filename;
      speech_and_gesture_video_mismatched_source.src = mismatched_filename;

      speech_and_gesture_span_text.innerHTML = text;
      speech_and_gesture_transcript.innerHTML = transcript_speech_and_gesture[id];

      speech_and_gesture_video_matched.load();
      speech_ang_gesture_video_mismatched.load();
  }
</script>

<table class="tg">
<thead>
    <tr>
      <th class="tg-0pky">Text prompt #</th>
      <th class="tg-0pky">NAT</th>
      <th class="tg-0pky">DIFF</th>
      <th class="tg-0pky" colspan="2">MA</th>
      <th class="tg-0pky">SM</th>
    </tr>
    <tr>
      <th class="tg-0pky">Solver steps</th>
      <th class="tg-0pky">-</th>
      <th class="tg-0pky">50 & 500</th>
      <th class="tg-0pky">50</th>
      <th class="tg-0pky">500</th>
      <th class="tg-0pky">500</th>
    </tr>
  </thead>
<tbody>
  <tr>
    <td>1</td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/NAT_C4_3_eval_0150_matched.mp4', 'stimuli/speech-and-gesture/NAT_C4_3_eval_0150_mismatched.mp4' ,'NAT 1')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/DIFF_C4_3_eval_0150_matched.mp4', 'stimuli/speech-and-gesture/DIFF_C4_3_eval_0150_mismatched.mp4' ,'DIFF 1')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_50_C4_3_eval_0150_matched.mp4', 'stimuli/speech-and-gesture/MAT_50_C4_3_eval_0150_mismatched.mp4' ,'MA-50 1')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_500_C4_3_eval_0150_matched.mp4', 'stimuli/speech-and-gesture/MAT_500_C4_3_eval_0150_mismatched.mp4' ,'MA-500 1')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/SM_500_C4_3_eval_0150_matched.mp4', 'stimuli/speech-and-gesture/SM_500_C4_3_eval_0150_mismatched.mp4' ,'SM-500 1')" />
    </td>
  </tr>
  <tr>
    <td>2</td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/NAT_C3_7_eval_1074_matched.mp4', 'stimuli/speech-and-gesture/NAT_C3_7_eval_1074_mismatched.mp4' ,'NAT 2')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/DIFF_C3_7_eval_1074_matched.mp4', 'stimuli/speech-and-gesture/DIFF_C3_7_eval_1074_mismatched.mp4' ,'DIFF 2')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_50_C3_7_eval_1074_matched.mp4', 'stimuli/speech-and-gesture/MAT_50_C3_7_eval_1074_mismatched.mp4' ,'MA-50 2')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_500_C3_7_eval_1074_matched.mp4', 'stimuli/speech-and-gesture/MAT_500_C3_7_eval_1074_mismatched.mp4' ,'MA-500 2')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/SM_500_C3_7_eval_1074_matched.mp4', 'stimuli/speech-and-gesture/SM_500_C3_7_eval_1074_mismatched.mp4' ,'SM-500 2')" />
    </td>
  </tr>
  <tr>
    <td>3</td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/NAT_C4_2_eval_0137_matched.mp4', 'stimuli/speech-and-gesture/NAT_C4_2_eval_0137_mismatched.mp4' ,'NAT 3')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/DIFF_C4_2_eval_0137_matched.mp4', 'stimuli/speech-and-gesture/DIFF_C4_2_eval_0137_mismatched.mp4' ,'DIFF 3')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_50_C4_2_eval_0137_matched.mp4', 'stimuli/speech-and-gesture/MAT_50_C4_2_eval_0137_mismatched.mp4' ,'MA-50 3')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_500_C4_2_eval_0137_matched.mp4', 'stimuli/speech-and-gesture/MAT_500_C4_2_eval_0137_mismatched.mp4' ,'MA-500 3')" />
    </td>
    <td>
      <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/SM_500_C4_2_eval_0137_matched.mp4', 'stimuli/speech-and-gesture/SM_500_C4_2_eval_0137_mismatched.mp4' ,'SM-500 3')" />
    </td>
    </tr>
    <tr>
      <td>4</td>
      <td>
        <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/NAT_C4_2_eval_0011_matched.mp4', 'stimuli/speech-and-gesture/NAT_C4_2_eval_0011_mismatched.mp4' ,'NAT 4')" />
      </td>
      <td>
        <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/DIFF_C4_2_eval_0011_matched.mp4', 'stimuli/speech-and-gesture/DIFF_C4_2_eval_0011_mismatched.mp4' ,'DIFF 4')" />
      </td>
      <td>
        <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_50_C4_2_eval_0011_matched.mp4', 'stimuli/speech-and-gesture/MAT_50_C4_2_eval_0011_mismatched.mp4' ,'MA-50 4')" />
      </td>
      <td>
        <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/MAT_500_C4_2_eval_0011_matched.mp4', 'stimuli/speech-and-gesture/MAT_500_C4_2_eval_0011_mismatched.mp4' ,'MA-500 4')" />
      </td>
      <td>
        <img src="images/play_button_black.png" height=40 onclick="play_speech_and_gesture_eval('stimuli/speech-and-gesture/SM_500_C4_2_eval_0011_matched.mp4', 'stimuli/speech-and-gesture/SM_500_C4_2_eval_0011_mismatched.mp4' ,'SM-500 4')" />
      </td>  
    </tr>
</tbody>
</table> -->