# RxJS wrapper for Text-to-Speech

```
npm i rxjs-tts
```

Try it online: https://stackblitz.com/edit/rxjs-tts?file=index.ts

## About

This is a RxJS wrapper around browser native [SpeechSynthesis](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis).

It provides handy interface for chaining and aborting TTS.

## Usage

```js
import { speak } from 'rxjs-tts';

speak('Hello!').subscribe();
```

## Chained

```js
import { speak } from 'rxjs-tts';

concat(
  speak('Hello, mom!'),
  speak('How are you?'),
  speak('I miss you.')
)
  .subscribe();
```

## Advanced usage

```js
import { of, merge, concat, timer } from "rxjs";
import { map, takeUntil } from "rxjs/operators";
import { speak, SpeechSynthesisUtteranceConfig } from "rxjs-tts";

const a: string = "Hello, mom!";

const b: SpeechSynthesisUtteranceConfig = {
  text: "How are you?",
  lang: "en-UK",
  pitch: 1,
  rate: 1,
  volume: 1
};

const c = new SpeechSynthesisUtterance("I miss you");
c.rate = 1;
c.lang = "en-US";
c.pitch = 1;
c.rate = 1;
c.volume = 1;

concat(
  speak(a),
  speak(b),
  speak(c)
)
.subscribe((e: SpeechSynthesisEvent) => {
  console.log(e.name);
  console.log(e.type);
});
```
