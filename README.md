# modern-sam

### a slightly better version of SoftVoice's Software Automatic Mouth

## what?

This is a slightly improved version of Commodore SAM based
off [discordier's SAM JS port](https://github.com/discordier/sam)

## why?

I wanted to incorporate SAM into my discord
bot, [MediaForge](https://github.com/HexCodeFFF/mediaforge), 
but the [C ports](https://github.com/s-macke/SAM) are too limiting as
they're essentially
instruction-for-instruction clones of software from the 80s: i.e. memory
limits everywhere. discordier's JS port has no such limitations, but
also didn't have everything I wanted it to. hence: this project which is
used by my [sam-cli project](https://github.com/HexCodeFFF/sam-cli)

## what's new?

- `SamJs.renderwav()`: like a mix between the existing `buf8`
  and `download` options: generates the full data for a valid WAV file
  and simply passes back the data for you to handle
- **advanced pronunciation**: new `moderncmu` option which, when
  enabled, uses
  [The Carnegie Mellon University Pronouncing Dictionary (CMUDict)](https://www.npmjs.com/package/@stdlib/datasets-cmudict)
  and [to-words](https://www.npmjs.com/package/to-words) to pronounce
  words more accurately. CMUdict is used to get correct pronunciation _
  and stress patterns_ for over 100k english words, while to-words
  allows SAM to fully read out any number
- unlimited speech: this isn't something unique to this project (comes
  from discordier's port), but it's worth mentioning since the C ports
  dont have it.

## usage

should be completely backwards compatible with discordier's
port: [usage for that is documented here](https://github.com/discordier/sam#usage)

worth mentioning are the config options, since they aren't mentioned in
the original readme. pass these as a dict into the `new SamJs()`
constructor
```js
/**
 * @param {Boolean} [options.phonetic]  Default false.
 * @param {Boolean} [options.singmode]  Default false.
 * @param {Boolean} [options.moderncmu] Default false.
 * @param {Boolean} [options.debug]     Default false.
 * @param {Number}  [options.pitch]     Default 64.
 * @param {Number}  [options.speed]     Default 72.
 * @param {Number}  [options.mouth]     Default 128.
 * @param {Number}  [options.throat]    Default 128.
 */
```
