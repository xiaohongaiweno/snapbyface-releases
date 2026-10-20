# How Video Editors Can Find Every Moment a Person Appears in Footage

A photo editor can scroll. A video editor cannot.

When a client asks for "every clip where the CEO is on screen" or "the part where my daughter walks in", the usual answer is to open the timeline and scrub. Ten minutes of footage is tolerable. Two hours of ceremony coverage, forty hours of interview rushes, or a season of event recordings is not — and scrubbing is the kind of work that scales badly: it takes longer every time the archive grows, and it has to be repeated for every new request.

Text search does not help here. There is nothing to grep in a video file. Filenames, folders and timecodes describe where a clip was stored, not who is in it.

Face search does help, and it works best when it runs on the machine that already has the footage.

## The approach that actually works

Video face search is not magic; it is the manual method, automated:

1. **Sample the video.** Look at the footage about once per second, so a person walking through the shot is still caught without analysing all thirty frames in between.
2. **Detect and encode faces** in each sampled moment.
3. **Compare each moment against a reference photo** of the person and keep the ones that are close enough.
4. **Merge consecutive hits into time ranges.** Twenty matching moments in a row become one entry — an appearance from 02:14 to 02:34 — instead of twenty separate results.

That last step is what makes the output usable. A raw list of frame numbers is technically correct and practically worthless; time ranges tell you where to put the playhead.

## A practical workflow

### 1. Start with one good reference photo per person

One clear, front-facing photo is enough to start. A passport-style shot or a well-lit headshot works better than a group photo, a sunglasses shot, or a frame grabbed from the footage itself.

If you have several people to find — a bride and groom, a panel of speakers, a cast — put each reference photo in a folder, one file per person. Name the file after the person. That folder becomes your people library, and the file names become the names you search by.

Bad reference photos are worth fixing up front. Reference photos where no face is detected, or where several faces are detected, should be replaced before you index anything: a reference photo with two people in it cannot tell the software which one you meant.

### 2. Point the tool at the footage folders

Add the folders that hold the material. The scan is recursive, so a messy folder tree that has accumulated over years is fine — you do not need to reorganise anything first.

Photos and video go into the same index. Supported photo formats include JPG/JPEG, PNG, BMP, TIFF, WebP and HEIC/HEIF (the default iPhone format). Supported video formats include MP4, MOV, AVI, MKV, M4V, WebM and TS. Camera RAW files (CR2, NEF, ARW and similar) are not supported, so index the exported copies rather than the RAW originals.

One detail that saves real time: when a scan meets files it cannot handle, say so. Silently skipping them makes you think the search missed something, when in fact the file was never readable.

### 3. Let the index run in the background

Indexing long footage takes a while, and it should not hold your machine hostage. Useful behaviours to look for:

- Progress you can actually read, with separate counters for photos, video and faces.
- Pause, resume and stop, with everything already analysed kept.
- Recovery after an unexpected quit — the task should offer to continue where it stopped rather than start over.
- **Incremental re-indexing.** Adding next week's footage should not re-analyse last month's. Files that have not changed are skipped.

### 4. Read the timeline, then jump straight to the moment

The result view should group video hits per file and show the appearance ranges, rather than dumping hundreds of thumbnails. Click a result and the preview should open at the start of the appearance, not at 00:00 — that is the difference between "here is a file that probably contains them" and "put your playhead here".

When the ranges are too coarse for the cut you need, tighten the sampling interval. Sampling about once per second is the default and suits most footage; a tighter interval gives finer ranges and costs more processing time. Remember that a reported time is the moment that was sampled, not a frame-accurate mark — it gets you to the right neighbourhood, and you fine-tune by eye.

### 5. Export the source files, not a list

For handoff, what you usually need is the original media files collected in one folder, so they can be dropped into the editing project. Video files are exported whole rather than trimmed, which is the right default: you want the surrounding context when you cut, and you can always trim later.

## Tuning the results

Two controls matter more than any other:

- **Similarity threshold.** The default is a middle setting; raise it when you are getting false positives, lower it when someone is being missed. Changing it re-matches against the faces already indexed — it does not re-analyse your media, so experimenting costs seconds, not hours.
- **A second reference photo.** If a person looks very different across the footage — years apart, different styling, heavy makeup, a beard — one photo may not cover both appearances. Add another reference and the recall improves immediately.

## Where results will disappoint you

Worth knowing before you promise a client anything:

- **Fast cuts and heavy motion blur** produce moments where the face is not clear enough to match.
- **Very small faces in a wide crowd shot** are the hard case for any face search.
- **A brief appearance can fall between two samples**, especially at the default interval.
- **Heavy appearance change** relative to the reference photo pulls the score below the threshold.

A cheap way to set expectations: index one folder first and check the top hits against what you know is in that footage. It takes a fraction of the time and tells you whether your reference photos and threshold are right.

## The privacy argument for doing this locally

Client footage, interview rushes, anything with minors in it — a lot of what crosses an editor's desk comes with an implicit or explicit expectation that it stays put. Cloud video search means uploading tens of gigabytes and letting someone else's GPU process it. For many projects, that is not an option you can offer the client, and often the upload alone takes longer than the analysis would.

**[SnapByFace](https://snapbyface.com/)** runs the whole pipeline on your own computer: detection, matching and the index live locally, your media is read but never modified, and the local database sits in `~/.snapbyface/`. No video, no frame and nothing about the faces in them is uploaded. The only outbound data is an optional device statistics ping containing no filenames and no media — and it can be switched off in Settings.

## Getting started

- Add a reference photo folder — one clear photo per person.
- Add the folders holding your footage.
- Let the index run; it pauses, resumes and continues after a restart.
- Read the appearance ranges and jump the preview to each one.
- Export the matched source files into a folder for the edit.

Unactivated, SnapByFace still runs the full local search but shows a limited number of matches — enough to tell whether it finds the person in your footage before you commit to anything. See [video face search](https://snapbyface.com/video-face-search/) for a fuller walkthrough, or [download SnapByFace](https://snapbyface.com/download/) and index one folder.

---

*Match quality depends on footage quality, reference photos and threshold settings. Test on a single folder before relying on it for a delivery deadline.*
