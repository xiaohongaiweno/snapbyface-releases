# How Event Photographers Can Help Guests Find Their Own Photos

After every event, the messages arrive.

"Can you send me the ones with me in them?" "Do you have any of my parents?" "I need a photo of me with the keynote speaker for LinkedIn." "Any chance you have a shot of our table?"

Each request is reasonable. Answering them by hand is not: it means opening a gallery of 1,500 frames from a wedding, 3,000 from a school sports day, or 6,000 from a conference, and looking for one face. Do that ten times and an evening is gone — unpaid, unbudgeted, and the least interesting way to spend it.

Face search turns those requests from a search problem into a lookup.

## Three ways this usually gets handled

**Manual.** You remember roughly where the shot was and scroll. Works when you shot it yourself an hour ago, fails three weeks later, and fails completely when an assistant or a second shooter took the photos.

**A cloud gallery with face tagging.** Convenient for guests, but it means uploading every photo to a third party, and the tagging quality and privacy terms are out of your hands. For school events, corporate events, medical or legal conferences, and anything involving minors, "we uploaded everyone's photos to a face recognition service" is often not an answer you are permitted to give. It also costs you the upload time on a 40 GB card.

**Local face search.** You keep the photos on your own drive, search by reference photo, and send each person only their own images. The privacy conversation gets much shorter, and the upload disappears entirely.

## The workflow

### Before the event: decide whose faces you will need

You cannot know every guest in advance, but you usually know the people who will generate requests:

- The couple, and both sets of parents.
- The keynote speakers, panellists, award winners and organisers.
- The client's VIP list.
- Staff and volunteers, if they want photos for their own channels.

Collect one clear photo of each — headshots from the event brief, a company page, or a photo you took on the day. Put them in a folder, one file per person, named after them. That folder is your people library.

For a wedding, that might be six photos. For a conference, twenty. The point is that the people who generate the most requests are set up before you start, so answering them later is a click.

### After the event: index once

Copy the card off, back it up, and add the event folder to the search tool. Photos and video go into the same index, so the ceremony video and the stills are searchable together:

- Photos: JPG/JPEG, PNG, BMP, TIFF, WebP, HEIC/HEIF.
- Video: MP4, MOV, AVI, MKV, M4V, WebM and TS.

Camera RAW files are not supported, so index the exported JPGs, not the RAW originals.

The first index of a large event takes a while; run it while you do something else. It can be paused and resumed, keeps whatever it has already analysed, and offers to continue after an unexpected quit.

### Answering a request

A guest emails asking for their photos. Two ways to handle it:

**If you already have their face in the library** — search their name, review the hits, export. Done in under a minute.

**If you do not** — ask them to send any recent photo of themselves, drop it into the people library, and search. Adding a person is matched against the faces already indexed; it does not re-analyse the event folder, so this takes seconds rather than another indexing run.

Then export: the matched original files are copied into a folder named after the person, ready to send.

### Letting guests search for themselves

Some photographers go further and run the lookup at the event. Set up a laptop with the index built, have guests provide a selfie or let them pick one of the "unknown faces" the software found, and show them their own photos on the spot.

That is where face clustering earns its keep: after indexing, the tool groups the faces it found but cannot name, and shows them as clusters. Recognise a group as "the groom's brother", name it, and every photo of him becomes searchable across the whole event. It also surfaces people you would never have thought to add — the person who turns out to be in forty frames.

Be careful with very large clusters. When a group contains an implausible number of faces, it usually means several similar-looking people were merged into one; only name it if you are confident.

## Why local matters here specifically

Event photography is a business built on trust, and the material is sensitive by default: children at school events, guests at private celebrations, attendees at professional conferences where being photographed at all may be a condition of registration.

Processing the images on your own computer means:

- **No upload.** No gallery service holds copies of everyone's face.
- **No third-party face database.** Nothing about your subjects leaves the machine.
- **A short privacy answer.** "The photos never leave my computer" is a sentence clients understand and accept.
- **Originals untouched.** Files are read, not modified — no renaming, moving or re-encoding of the deliverables.

**[SnapByFace](https://snapbyface.com/)** is built this way: recognition and search run locally, the index is stored on your machine in `~/.snapbyface/`, and the only outbound data is an optional device statistics ping with no filenames or media, which can be switched off.

Get consent for the photography itself, and check what your client's venue or organisation requires. Local processing makes that conversation easier; it does not replace it.

## Tuning for event conditions

Event lighting and volume produce the same problems every time. The two controls worth knowing:

- **Similarity threshold.** The default is a middle setting. Raise it if you are seeing people who are not there; lower it if you are missing a guest who is mostly photographed in profile, in low light, or in a crowd. Changing it re-matches against faces already found rather than re-running the analysis, so trying both costs seconds.
- **A second reference photo.** A guest who looks completely different in evening dress versus the office headshot you were given is the classic miss. Add both.

Also expect honest limits: fast-moving shots with motion blur, faces that are very small in a wide crowd frame, and brief appearances in video can all be missed. Video hits are reported as appearance ranges based on sampling — roughly once per second by default — so the timestamp gets you to the right moment, not to an exact frame.

## Turning this into a deliverable

Once searching is cheap, it becomes something you can sell rather than absorb:

- **Per-person galleries** as an add-on for weddings and conferences.
- **VIP packages** — "every frame your speaker appears in, delivered within 24 hours".
- **Staff and volunteer photos** for the organiser's own social channels.
- **Same-day lookup desk** at the event itself.

The economics change because the marginal cost of one more person drops to almost nothing. Indexing is the expensive step and you pay it once per event.

## Getting started

1. Collect one clear photo per VIP into a folder, named after each person.
2. Add the event folder and index it.
3. Search the people you set up; check the top hits look right.
4. Name a few unnamed face clusters to cover everyone else.
5. Export per person and send.

Unactivated, SnapByFace runs the full local search and shows a limited number of matches — enough to test it on last weekend's event before using it on a paid booking. See [photo face search](https://snapbyface.com/photo-face-search/) and [video face search](https://snapbyface.com/video-face-search/) for detail, or [download SnapByFace](https://snapbyface.com/download/) and index one event folder.

---

*Check consent and delivery requirements with your client before sharing photos of identifiable people. Local processing reduces privacy risk but does not remove your obligations.*
