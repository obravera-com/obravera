# What's new in ObraVera

Every version, newest first. Each version's full release notes, and its
downloads, are on the
[Releases page](https://github.com/obravera-com/obravera/releases).

---

## 0.8.0 (September 2026)

**The phone release.** A work can now be checked by holding a phone up to a
speaker at [verify.obravera.com](https://verify.obravera.com), not only by
checking the file on a computer.

**New**
- **Check a work by phone.** Each registration now carries an acoustic
  fingerprint, so a recording made through a microphone can be recognised.
- **Add fingerprints to earlier works** (API Key Management). Gives works
  registered before this version a fingerprint, without changing or
  re-exporting the audio.
- **Register existing works** (API Key Management). Registers works the server
  doesn't have yet, such as ones embedded while offline. **Only your own works
  are registered**; a file carrying another creator's credential is listed and
  left alone.
- **Works in several files (audiobook chapters)**: every chapter can now be
  recognised by phone, not just the first.
- **Update notice**: the app tells you when a newer version is available. It
  never downloads or installs anything.
- **Downloads move here**, signed and notarised, with checksums
  ([how to check a download](https://github.com/obravera-com/obravera#verifying-a-download)).

**Changed**
- **Default embed strength is now 15** (was 10), for reliable recognition over a
  microphone. Measured cost: −3.53 dB SNR. Existing files are unaffected.
- **Embedding registers the work** automatically, including from the command
  line.
- **AudioSeal-only works** are registered too. A phone check reports them as
  "Recognised, not verified", and the app warns you when you choose it.
- **Clearer reports**: register and attach name every file that needs your
  attention, and why. Messages about API keys distinguish a rejected key, too
  many attempts, and an unreachable server.

**Fixed**
- Intel Macs: a first launch could switch to AudioSeal on its own, and
  AudioSeal was far slower than it should be.
- Windows: saving an API key could report an error although it had been saved.
- A stale copy of your API key could overwrite a newer one.
- The folder-watching agent now stops cleanly and says what to do.

**Known limitations**
- The Windows kit isn't code-signed yet.
- On long files the window can show "Not Responding" while it works. Leave it
  to finish; this is addressed in 0.8.1.

**Open source**: each download includes `THIRD-PARTY-NOTICES.txt`; sources are
at [Third-party sources for ObraVera 0.8.0](https://github.com/obravera-com/obravera/releases/tag/third-party-sources-0.8.0).

---

## 0.7.1 (June 2026)

**Fixed**
- The folder-watching agent runs from the installed app and uses its bundled
  tools, instead of needing them installed separately.
- The agent follows the preset's ISCC setting and passes on its operator ID,
  studio ID and AI-usage declaration.

---

## 0.7.0 (June 2026)

**New**
- **French.** The whole app is translated, with the language switchable in the
  app and in macOS System Settings.
- **Folder watching.** Drop files into a watched folder and ObraVera watermarks,
  signs and registers them in the background, using your Quick Apply preset.

---

## 0.6.0 (May 2026)

**New**
- **Compilations.** Combine several watermarked sources into one work (the
  Compile tab, or `obravera compile`), keeping the attribution of every part.
  Verify shows each part's declared and detected watermark side by side.

**Changed**
- Clearer API-key error messages.

**Fixed**
- Windows: audiowmark could fail on machines without certain runtime files; the
  kit now includes them and tests the watermarking tools during installation.

---

## 0.5.0 (April 2026)

**New**
- **verify.obravera.com**, the online verifier, and the app points to it out of
  the box.
- Works offline: AudioSeal's model is included, so the first embed no longer
  needs a download.
- A build for Intel Macs.

**Changed**
- The AudioSeal watermark's error-correction layout changed to fix a rare silent
  error. Older AudioSeal watermarks are still read.
- Batch embed shows which file it's working on as it starts, not after.

---

## 0.4.0 (April 2026)

**New**
- The first packaged Mac app.
- **Embed presets**: save, edit and apply your usual settings in one click.
- API Key Management in its own tab.

---

Earlier versions were internal test builds.
