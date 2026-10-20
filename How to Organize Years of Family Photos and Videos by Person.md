# How to Organize Years of Family Photos and Videos by Person

Most family photo collections are not disorganised. They are duplicated, scattered, and slightly different on every device.

There is the phone's camera roll, the laptop's Pictures folder, an old external drive, a cloud export from a service you cancelled, a chunk of DVDs from a camcorder era, and a shared album someone else started. Between them, fifteen years of birthdays and holidays.

Finding "all the photos of Grandma" in that should be easy — she is in hundreds of them. In practice it means opening folders at random and hoping, because no one has ever tagged anything and nobody remembers which drive the 2014 summer is on.

Face search solves this specific problem well, and doing it locally suits family material better than doing it in the cloud.

## Step 1: Gather, but do not reorganise

The instinct is to sort everything into a perfect folder tree first. Resist it — reorganising is the part people never finish.

Copy what you can into one place, keeping it simple:

```text
Family Archive/
├── 2010-2015/
├── 2016-2020/
├── 2021-2026/
├── Old-DVD-Rips/
└── People/          # reference photos, one per person
```

Two rules:

- **Work on a copy.** Keep the originals where they are until you are sure the new structure is right.
- **Do not rename or move anything yet.** Search finds files by content; it does not need tidy names.

Duplicates are not a problem at this stage. Search will surface both copies of a photo, which is mildly annoying and far better than losing one.

## Step 2: Build a small people library

Create one folder with a single clear photo per person — one passport-style shot, one school photo, one well-lit headshot. Name each file after the person:

```text
People/
├── Grandma-Chen.jpg
├── Dad.jpg
├── Mum.jpg
├── Mei.jpg
└── Little-Ben.jpg
```

That folder is the whole setup. Each photo becomes one searchable person, and the file name becomes their name in the results.

Two things to get right:

- **Use one face per photo.** A family photo with four people in it cannot say which of them you meant. If the tool flags a photo as containing several faces, replace it with a single-face shot.
- **Front-facing and well-lit beats flattering.** A slightly dull passport photo matches far better across fifteen years than a stylish profile shot.

This is also the step that catches unusable photos early: if no face is detected in a reference photo, you find out before indexing anything, not after.

## Step 3: Index once, then add as you go

Point the tool at the archive folders and let it index. It walks them recursively, so the messy year folders and the DVD rips can all be added at once.

Photos and videos are indexed together. Supported photo formats include JPG/JPEG, PNG, BMP, TIFF, WebP and HEIC/HEIF — which matters, because HEIC is the default format on iPhones and a surprising share of a modern family archive is invisible to tools that cannot read it. Supported video formats include MP4, MOV, AVI, MKV, M4V, WebM and TS, so old camcorder files ripped to MP4 and phone videos both work.

Home video is where the payoff is largest. Instead of scrubbing through forty minutes of a birthday party, you get the appearance ranges — where someone is on screen and for how long — and can jump straight to those moments.

The first index is the slow one. After that:

- **Adding new photos is incremental.** Drop this year's photos in and rescan; what has not changed is skipped.
- **Adding a person does not re-analyse anything.** Drop a new reference photo into the people library and it is matched against the faces already indexed.

## Step 4: Let the archive tell you who is in it

The people you think to search for are not the only ones in there. Relatives who died years ago, a child's friends, a neighbour who appeared at every barbecue for a decade — you will not remember them all, and you should not have to.

A useful feature here is face clustering: the tool groups the faces it found but could not name, and shows them to you as clusters. Recognise one, name it, and every photo and video containing that face becomes searchable immediately. It turns "who else is in this archive?" into a question you can answer in an afternoon rather than a research project.

Be slightly careful with large clusters. If a group contains an implausible number of faces, it usually means two or three similar-looking people were merged; give it a name only if you are confident, otherwise leave it.

## Step 5: Export per person

Once you have results, the useful output is files, not screenshots.

Pick a person, get their matches, and copy the matched original files into a folder:

```text
Delivery/
├── Grandma-Chen/     # every photo and video she appears in
├── Little-Ben/       # 11 years of one child, in one folder
└── Mei/
```

That is what makes the archive usable for other people — you can hand a relative a folder of everything they are in, or build a slideshow from a decade of one child without hunting.

Note that a matched video is exported as the complete original file rather than a trimmed clip. For family video that is usually what you want; trimming is easy later, recovering context you did not export is not.

## Step 6: Tune only if you need to

The default similarity setting is a reasonable middle ground. Two situations justify changing it:

- **Too many false positives** — someone is being found in photos they are not in. Raise the threshold.
- **Someone is being missed** — a child who has changed enormously, or a relative photographed mostly in profile or in poor light. Lower the threshold, or add a second, more recent reference photo.

Changing the threshold re-matches against faces already found; it does not re-analyse your media. So it costs seconds to try, and you can go back just as easily.

## Why this belongs on your own computer

Family archives are exactly the kind of material people do not want on someone else's server: children, private moments, documents that got photographed by accident, and thousands of frames of ordinary domestic life.

**[SnapByFace](https://snapbyface.com/)** does the recognition and search locally. Photos, videos and face data stay on your machine, the index lives in `~/.snapbyface/`, and your original files are read but never modified — nothing is renamed, moved or re-encoded. Nothing is uploaded; the only outbound data is an optional device statistics ping that carries no files and can be turned off in Settings.

Because it is local, it also works on an archive that lives on an external drive, and it works without a fast connection — which matters when the archive is 200 GB and your upload speed is not.

## A realistic first session

1. Copy the archive into one folder (keep the originals).
2. Make a `People/` folder with one clear photo per person.
3. Add both to [SnapByFace](https://snapbyface.com/) and index.
4. Search one person. Check whether the top hits look right.
5. Name a few unnamed face clusters.
6. Export per person into folders.

You do not need to finish. Half-organised and searchable beats perfectly-organised and never started — once the index exists, every future search is a few seconds.

See [photo face search](https://snapbyface.com/photo-face-search/) and [video face search](https://snapbyface.com/video-face-search/) for more detail, or [download SnapByFace](https://snapbyface.com/download/) and try it on one folder.

---

*Back up your archive before reorganising anything. Local processing keeps your files private, but it does not replace a backup.*
