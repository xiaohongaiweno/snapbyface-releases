# Offline Face Search for Sensitive Photos and Videos

Some material can be searched, but not uploaded.

A documentary interview with a source who asked for anonymity. Client footage under NDA. Photographs of minors at a school. Medical or legal imaging case photos. HR material. Anything a journalist, investigator, lawyer, clinician, researcher or archivist holds on behalf of someone else.

In all of these, finding a person across a large collection is genuinely useful — and handing that collection to a cloud service is not something you are allowed to do. Which usually means the search never happens, and someone scrubs through forty hours of footage by hand instead.

Local face search removes the trade-off. The useful question is not "is it private?" — every tool claims that — but what "local" actually guarantees.

## What "local" has to mean

Before trusting any tool with sensitive material, check each of these. They are separable; a product can satisfy some and not others.

**1. The analysis runs on your machine.**
Not "processed on our secure servers". The models should be bundled with the application and executed locally, with no media sent anywhere at any point.

**2. No upload, at all, ever.**
Including thumbnails, including "temporary processing copies", including for "quality improvement". If the workflow requires an account, be suspicious of what the account is for.

**3. Your original files are not modified.**
A search tool should read your media. It should never rename, move, re-encode or rewrite it — for sensitive material, an unmodified chain of custody matters, and modified files can break checksums used as evidence.

**4. The derived data stays local too.**
Face data is biometric data. The index, the embeddings and the search history should be files on your machine, in a location you can find, inspect and delete.

**5. Any network activity is enumerated and optional.**
There should be a short, written list of every outbound request, and a switch that stops all of them.

**6. It works disconnected.**
If it cannot run on an air-gapped or offline machine, it is not really local — it is cloud-assisted.

## How SnapByFace behaves on each point

**[SnapByFace](https://snapbyface.com/)** is a desktop application for Windows and macOS built around local processing. Concretely:

- **Recognition runs locally** using models bundled with the app. The inference runs on the CPU; there is no GPU requirement and no remote inference call.
- **Nothing is uploaded.** No photo, no video, no frame, and nothing derived from the faces in them.
- **Original media is read-only.** Files are never renamed, moved or re-encoded.
- **The index is a local file.** Database, configuration and logs sit in `~/.snapbyface/` — a directory you can inspect, back up or delete.
- **One optional outbound request.** A device statistics ping containing machine code, app version, operating system, language and activation state — no filenames, no media, no search activity. It is off if you turn it off in Settings, and turning it off also requests deletion of that machine's records server-side.
- **Activation works offline.** Licences are bound to a machine code and verified locally against a signature, so the machine code can be sent out of band and the key pasted in without an account.

Nothing else needs the network. Activation itself is verified locally against a signature, so pasting a licence code works with the cable unplugged — only buying one happens in a browser. What remains is the optional statistics ping above and a manual "check for updates" action, which only reports a version number and links to the download page — it never auto-installs.

## Working with sensitive collections

### Keep the media where it is

You do not need to import anything into a catalogue or move files into a managed library. Point the tool at the folder — including a folder on an external or encrypted drive — and it reads from there. Your existing storage layout, permissions and encryption stay as they are.

Photos and video are indexed together: JPG/JPEG, PNG, BMP, TIFF, WebP and HEIC/HEIF for images; MP4, MOV, AVI, MKV, M4V, WebM and TS for video. RAW camera files are not supported, so work from exported copies.

If a scan meets files it cannot read, it should tell you which ones and why. Silently skipping them is worse than useless here: in a sensitive review, "no hits" and "never looked" must not look the same.

### One reference photo, minimal footprint

A single clear, front-facing photo of the person is enough to search an entire collection. For a source, subject or interviewee whose identity you must handle carefully, that means the only face data you need is one file you already control — no enrolment, no gallery of their images, no biometric record created for anyone else.

If recall is poor, add a second reference photo rather than lowering the threshold indiscriminately. A person who looks very different across a collection — years apart, different styling, poor lighting — is the usual cause.

### Tune without re-processing

The similarity threshold defaults to a middle setting and is adjustable. Raising it reduces false positives; lowering it catches more, including more mistakes. Changing it re-matches against faces already indexed and does not re-analyse the media — which matters for two reasons: you can calibrate in seconds, and you are not repeatedly reading sensitive files off disk.

Adding a new person works the same way. Nothing is re-read from the source media.

### Long-running work on large archives

Indexing a large archive takes time, so the operational details matter more than the features:

- Progress reporting you can read, plus pause, resume and stop.
- Everything already analysed is kept when you stop.
- After an unexpected quit, the task offers to continue where it stopped.
- Rescanning is incremental — files that have not changed are skipped, so re-running after adding material is cheap.

### Video without scrubbing

For interview rushes, recorded proceedings or surveillance-style footage, the output you want is time ranges: where a person is on screen and for how long. Consecutive matches are merged into a single appearance rather than reported as hundreds of separate frames, and opening a result jumps the preview to that moment.

Sampling is roughly one frame per second by default and can be tightened; the reported time is the sampled moment, so it gets you to the right place rather than to an exact frame. Fine-tune by eye from there.

### Exporting what you found

Export copies the matched original media files into a folder of your choosing — the complete original files, not re-encoded copies, and video exported whole rather than trimmed. For material where integrity matters, that is the correct behaviour: what you hand on is byte-identical to the source.

## A checklist for sensitive work

1. Confirm the tool runs the analysis locally, with bundled models.
2. Turn off any telemetry or statistics reporting in Settings.
3. Point it at the media where it lives; do not move or copy it unnecessarily.
4. Index once. Keep the index alongside the media if the project has a retention policy.
5. Search with a single reference photo. Add a second only if recall is poor.
6. Export matched originals to a separate folder for review or disclosure.
7. When the project ends, delete `~/.snapbyface/` — that removes the index, the face data and the logs together.

## Honest limits

Local search is not magic, and with sensitive material it is worth knowing where it fails before you rely on it:

- Motion blur, fast cuts and brief appearances can be missed.
- Very small faces in wide crowd shots are hard for any face search.
- Significant appearance change from the reference photo reduces recall.
- Video times are sampled moments, not frame-accurate marks.

Test on one folder first and check the results against what you know is in it. If the tool finds what a human finds, it is worth using; if not, know that before it matters.

## Getting started

The trial runs the full local search, so you can verify the behaviour on your own material without activating anything — useful when the first question you need answered is "does this touch the network?"

- [Offline face search](https://snapbyface.com/offline-face-search/) — how the local workflow works
- [Video face search](https://snapbyface.com/video-face-search/) — finding appearances in footage
- [Photo face search](https://snapbyface.com/photo-face-search/) — finding people in photos
- [Download SnapByFace](https://snapbyface.com/download/)

---

*Local processing keeps your material on your own machine. It does not by itself satisfy a legal, contractual or ethical obligation — check what your organisation, client or jurisdiction requires before indexing sensitive material.*
