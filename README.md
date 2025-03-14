# HmOog

A Node.js library to write out-of-game Hackmud scripts.

Currently, this only supports Windows, but macOS and Linux support will be added soon.

## Usage

```
pnpm i @sarahisweird/hmoog
```

Hackmud must be open for HmOog to work!

## Getting started

For more specialized stuff, check out the TSDocs of the `HmOog` class!

```ts
import { HmOog, waitMs } from '@sarahisweird/hmoog';

const oog = new HmOog();

// This must be called before any other calls!
await oog.init();

let millisecondsUntilHardline = await oog.enterHardline();
if (millisecondsUntilHardline > 0) {
    await waitMs(millisecondsUntilHardline);
    await oog.enterHardline();
}

// Do stuff in hardline

await oog.exitHardline();

const result = await oog.runCommand('accts.xfer_gc_to');
/*
{
    command: 'scripts.quine',
    success: false,
    output: {
        colored: {
            raw: 'Use <color=#FF8000FF>scripts</color>.<color=#1EFF00FF>quine</color> to output the source code of your script. Place the following into your script:\n' +
                'return #<color=#9B9B9BFF>fs</color>.scripts.quine()',
            lines: [
                'Use <color=#FF8000FF>scripts</color>.<color=#1EFF00FF>quine</color> to output the source code of your script. Place the following into your script:',
                'return #<color=#9B9B9BFF>fs</color>.scripts.quine()'
            ]
        },
        uncolored: {
            raw: 'Use scripts.quine to output the source code of your script. Place the following into your script:\n' +
                'return #fs.scripts.quine()',
            lines: [
                'Use scripts.quine to output the source code of your script. Place the following into your script:',
                'return #fs.scripts.quine()'
            ]
        }
    }
}
*/
```

## License

HmOog is licensed under MIT-0.
That means: do what you want with this, but don't yell at me if it breaks your computer, marriage or bank account.
You don't need to attribute anything to me either, but I'd appreciate it if you do it anyway :)

For the full license text, check [LICENSE.md](LICENSE.md).
