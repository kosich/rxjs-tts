<div align="center">
  <h1>
    <br/>
    🗣
    <br/>
    <sub><sub>Web API Text-to-Speech with RxJS</sub></sub>
    <br/>
    <br/>
    <a href="https://www.npmjs.com/package/rxjs-tts"><img src="https://img.shields.io/npm/v/rxjs-tts" alt="NPM"></a>
    <a href="https://bundlephobia.com/result?p=rxjs-tts@latest"><img src="https://img.shields.io/bundlephobia/minzip/rxjs-tts?label=gzipped" alt="Bundlephobia"></a>
    <a href="https://opensource.org/licenses/MIT" rel="nofollow"><img src="https://img.shields.io/npm/l/rxjs-tts" alt="MIT license"></a>
    <br/>
    <br/>
    <br/>
  </h1>
</div>

This is a RxJS wrapper around browser native [SpeechSynthesis](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis).

It provides handy interface for chaining and aborting TTS.

Try it [**online**](https://stackblitz.com/edit/rxjs-tts?file=index.ts)

## Install

```
npm i rxjs-tts
```

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
    speak('I miss you.'),
).subscribe();
```

## Advanced usage

```js
import { of, merge, concat, timer } from 'rxjs';
import { map, takeUntil } from 'rxjs/operators';
import { speak, SpeechSynthesisUtteranceConfig } from 'rxjs-tts';

const a: string = 'Hello, mom!';

const b: SpeechSynthesisUtteranceConfig = {
    text: 'How are you?',
    lang: 'en-UK',
    pitch: 1,
    rate: 1,
    volume: 1,
};

const c = new SpeechSynthesisUtterance('I miss you');
c.rate = 1;
c.lang = 'en-US';
c.pitch = 1;
c.rate = 1;
c.volume = 1;

concat(speak(a), speak(b), speak(c)).subscribe((e: SpeechSynthesisEvent) => {
    console.log(e.name);
    console.log(e.type);
});
```

## Enjoy 🙂
