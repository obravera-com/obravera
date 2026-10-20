# What's new in ObraVera

Every version, newest first. Each version's full release notes, and its
downloads, are on the
[Releases page](https://github.com/obravera-com/obravera/releases).

---

## 0.8.2 (October 2026)

**The Intel Mac fix.** The 0.8.1 download for Intel Macs doesn't open: by
mistake it was built on an Apple Silicon Mac. 0.8.2 is a proper Intel build,
and the build now refuses to continue if it finds this mistake. On an Apple
Silicon Mac or Windows, 0.8.1 works and there's no hurry to update.

**Fixed**
- **Intel Macs: the app opens.** 0.8.1's Intel download showed a white circle
  with a line through it.
- **Works embedded while the server is unreachable are queued and sent
  later**, instead of being reported "Not registered" and forgotten.
- One problem entry in that queue no longer holds up the rest; works the server
  refuses are set aside and shown to you with its reason; nothing is lost if a
  retry is interrupted, and the window no longer freezes while the queue is
  sent.

**Unchanged**
- The audio tools are the same as 0.8.1's, so watermarks and fingerprints are
  exactly as before. Your API key, works and settings carry over.

**Known limitations**
- The Windows kit is a pilot kit (run `install.ps1`); its scripts and tools are
  code-signed.
- On Windows, small black windows still flash briefly while you embed or
  verify. Harmless; 0.8.1 said this would be fixed in the next release, but
  0.8.2 is only the Intel fix, so it's now planned for 0.9.0.
- An MP3 embedded with AudioSeal alone may not verify. Use Standard
  (audiowmark), the default.
- AudioSeal is still slow on older Intel Macs.
- French translations of the new messages haven't been reviewed by a native
  speaker yet.

**Open source**: each download includes `THIRD-PARTY-NOTICES.txt`; sources are
at [Third-party sources for ObraVera 0.8.2](https://github.com/obravera-com/obravera/releases/tag/third-party-sources-0.8.2).

---

## 0.8.1 (October 2026)

**A maintenance release.** Every audio tool ObraVera ships is now built by us
from published source, the window stays responsive while it embeds, and a few
verification results now say what actually happened.

**New**
- **Verify shows the watermark strength** the work was embedded at. Works
  embedded before 0.8.1 show "not recorded".

**Changed**
- **Embedding no longer freezes the window.** It runs in the background, and a
  second click on Embed while it's working is ignored.
- **The strength range is advice, not a rule.** 5–20 is recommended (15 is the
  default); outside it the app warns you and goes ahead.
- **Audio tools built from published source** (audiowmark, FFmpeg, fpcalc).
  Existing works keep the same fingerprints and watermarks: checked on every
  platform before release.
- A file neither the old nor the new FFmpeg can properly decode now fails with
  an error instead of being credentialed as noise.

**Fixed**
- Verify in an open window finds works the folder-watching agent has just
  credentialed, without a restart.
- An unwatermarked copy of a work is reported as "recognised, not verified",
  not as a verified, edited copy.
- Verify finds watermarks in audio that has been sped up or slowed down
  (about 0.8× to 1.25×).
- Embedding only accepts WAV and MP3, and checks before it touches the file.
- The folder-watching agent registers the AI-usage declaration you chose.
- Clearer API key messages; verification reports show file text as plain text.

**Known limitations**
- The Windows kit is a pilot kit (run `install.ps1`); its scripts and tools are
  now code-signed.
- On Windows, small black windows flash briefly while you embed or verify.
  Harmless; fixed in the next release.
- An MP3 embedded with AudioSeal alone may not verify. Use Standard
  (audiowmark), the default.
- AudioSeal is still slow on older Intel Macs.
- French translations of the new messages haven't been reviewed by a native
  speaker yet.

**Open source**: each download includes `THIRD-PARTY-NOTICES.txt`; sources are
at [Third-party sources for ObraVera 0.8.1](https://github.com/obravera-com/obravera/releases/tag/third-party-sources-0.8.1).

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
  to finish, and don't click Embed again while it's busy: a second click
  starts a second embed. Addressed in 0.8.1.
- Single-file embed accepts WAV and MP3; convert other formats to WAV first.

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
