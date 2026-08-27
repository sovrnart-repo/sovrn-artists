# Pindar Van Arman — reference notes

Compiled from sovrn.art, which published *Reflection* and *byteGANs*. Written as
a companion to **raster.art/artist/pindar-van-arman/about**.

Two sections here are worth reading even if you use nothing else: the
**on-chain architecture of Reflection**, which is the substance of what the work
achieved and is hard to find stated anywhere accurately, and the **two handling
notes** at the end, which will save you a support ticket each.

---

## The artist

Pindar Van Arman (American) has collaborated with painting robots since 2006. He
works toward machines that paint like a child — the question underneath being
how a generative process escapes algorithmic determinism and reaches something
that can be called emergence.

Exhibited internationally. Featured in the documentary *Machine, The Art of
Intelligence* and in the NVIDIA AI Art Gallery. Held in the permanent collection
of **LACMA**. He co-runs Sovrn.

- <https://www.vanarman.com>

---

## The three works

| | *Reflection* | *byteGANs* | *Emerging Faces* |
|---|---|---|---|
| Released | 7 February 2024 | 20 February 2023 | 2017 |
| Works | 999 | 1,111 | 44 |
| Chain | Ethereum | Ethereum | Ethereum |
| Fully on-chain | yes | yes | yes |
| Contract | `0x5137cfB461d24040F5ce6B85D860c47A24f85412` | `0x45C67B2b81067911dE611e11FC5c7a4605cA4162` | no Sovrn release contract |
| Raster | `/artwork/reflection-by-pindar-van-arman` | `/artwork/bytegans-by-pindar-van-arman` | `/artwork/emerging-faces-by-pindar-van-arman` |

The work counts for *Reflection* and *byteGANs* are `totalSupply()` read from
the contracts themselves, not published claims. *Emerging Faces* is 44 canvases
from the 2017 experiment, catalogued by the artist.

*Reflection* has a **second contract**: *Nine Reflections*, June 2025,
`0xDe0B8F5FE80017F6a85c8ed15baB3EC3a6f49460`. It is the one the Francisco
Carolinum holds. Worth knowing before anyone assumes a single address covers the
work.

---

## Reflection, and what "on-chain" means here

A painting robot works in passes. It lays a ground, makes a mark, photographs
what the mark did, and answers it. The loop between those steps is what Van Arman
calls **Reflective AI**, and it is the practice of a decade.

Ordinarily that loop leaves nothing behind — the canvas is photographed when it
is finished and everything on the way to it is gone. **In *Reflection* the passes
are the artwork.** Each piece names its own, in sequence, inside the file:
background, circles, bytegan 20x20, touchups, ganStrokes, lighten, skull, darken,
background binary, highlight, skull flourish. Twenty-one passes are numbered in
all. Seven fade in across an eight-second loop — at two seconds, then 3.2, 3.6,
4.0, 4.4, 5.2 and six — so each piece rebuilds itself in the order the robot
built it.

Nothing is being played back. The sequence *is* the file, and the file is what
the contract holds.

### The resolution, and the problem it creates

A single piece is **92 KB of pure vector**: roughly 900 drawing elements, of
which **873 are paths**, and **no embedded raster at all**. There is no bitmap
inside it to degrade — the piece is geometry, and renders as precisely on a
gallery wall as on a phone.

That is what makes it hard. Ethereum caps any single contract at **24,576 bytes**
of code (EIP-170), enforced by consensus. One *Reflection* is nearly four times
that. A piece this size cannot live in a contract.

### So it lives in thirty-one

Tracing what a call to `tokenURI` actually reads, across twelve pieces sampled
through the collection, returns the same structure every time:

| | |
|---|---|
| Contracts read to render one piece | 31 |
| Shared by all 999 | 13 |
| Particular to that piece | 18 |
| Largest single data contract | 22,499 B — 91.5% of the limit |
| Contracts in the collection | ~136 |

Thirteen contracts form the engine every piece shares. The other eighteen hold
that particular painting, drawn from a common bank. The largest sits at 91.5% of
what Ethereum permits, which gives a fair sense of how hard the ceiling was being
pushed against.

All of that apparatus exists for one reason: it is what the detail costs once you
refuse to put the image anywhere but the chain. `tokenURI` returns a base64 SVG —
the artwork itself, no gateway, no IPFS, nothing to go dark.

Fuller account: <https://www.sovrn.art/curated/reflection/on-chain>

### One nuance about the fades

A minted piece carries seven fades. The artist's exhibition renders for the
Francisco Carolinum carry twenty to twenty-six, and only six of those renders
exist. **Seven is not a diminished file** — a minted piece carrying seven is the
work as it was composed. Worth saying plainly, because the comparison invites the
wrong conclusion.

---

## byteGANs

100% on-chain AI art, and deliberately tiny: **a kilobyte on the ledger.**

Each byteGAN is an **11×11 pixel animated GIF**, 11 frames, about 2.2 seconds,
wrapped in SVG at 500px with pixelated rendering — around **1.1 KB** in total.

Three major types embody three intelligences:

- **skullGANs** — Evolutionary Intelligence
- **cyberGANs** — Artificial Intelligence
- **octoGANs** — Decentralized Intelligence

plus a small subset of rarer types.

byteGANs grew out of the **bitGAN Collabs**, the collective first drop that also
gave rise to Sovrn Open, Sovrn's strand for emerging artists.

---

## Emerging Faces

In 2017 Van Arman trained a GAN to recognise faces, paired it with
aesthetic-evaluation algorithms, gave his robot a camera so it could watch its
own strokes, and then **removed himself from the process** — instructing the
machine and letting it work.

44 canvases. Presented on the artist's own site rather than a sovrn.art
collection page, and it carries no Sovrn release contract, so treat its
provenance separately from the other two.

Exhibition history: **Robot Art 2018 (First Place)**; Seoul, MBN Y Forum, 2018;
Berlin, Aspen AI Conference, 2018; London, *Art of the Machine*, 2019; New York,
*Beyond Species*, 2019; LACMA permanent collection, 2023; New York, *Augmented
Intelligence* group auction, 2025.

- <https://www.vanarman.com/emergence>

---

## Museums, and recognition

**LACMA — permanent collection.** *AI Imagined Portrait Painted by a Robot #2*
(2018), from the series that took first place in the $100,000 International Robot
Art Contest in 2018. Every brush stroke was calculated and executed by a robot,
bringing the image temporarily into the physical world. **The canvas has since
been destroyed, and the work has returned to this purely digital form** — which
is the part most accounts leave out and the part that gives the piece its point.
Donated by The Cozomo de' Medici Collection; announced 13 February 2023.
<https://www.sovrn.art/collections/lacma>

**Museum of Crypto Art — permanent collection.** *Five Reflections*: five works
from *Reflection*. <https://www.sovrn.art/collections/moca>

**Francisco Carolinum, Linz.** Holds the Sovrn full set, including *Nine
Reflections*. <https://www.sovrn.art/collections/fransisco-carolinum>

*Reflection* has also been presented by **MoA+L** and **Iconic**.

### Two placements that are not documented on sovrn.art

Both of these are real and sourced, but they come from our submission corpus
rather than from our own site, so I have given you the primary source to check
rather than asking you to take our word for it.

**Lumen Prize 2025** — *Reflection*, finalist in the Still Image category.
<https://lumenprize.org/2025-still-image-finalists/pindar-van-arman>

**ART OF PUNK** — Francisco Carolinum, Linz, and the metaverse Voxels;
OÖ Landes-Kultur GmbH, 4 September 2024 – 26 January 2025, curated by Julia
Staudach. Billed as the world's first museum exhibition of artists from the
CryptoPunk community — only artists who own one or more CryptoPunks. Van Arman
was among them, alongside Martin Lukas Ostachowski. Same venue and curator as the
Sovrn Full Ethereum Set, but a separate exhibition.
<https://www.ooekultur.at/en/exhibitions-events/art-of-punk>

---

## Two handling notes

These are both things we hit ourselves, and both cost time to diagnose.

**1. Reflection token ids are zero-based; the artist's list is not.** The list
runs 1–999 and the token ids run 0–998, so **id = list number − 1**. Anyone
reading a number off a title card and querying it directly gets the neighbouring
work, and there is no error to tell them. Our own tooling explains the off-by-one
rather than failing silently, because everybody makes this mistake once.

**2. byteGAN #469's metadata is malformed on-chain.** One `attributes` entry has
an unquoted key — `{trait_type:"subtype",…}` — so `JSON.parse` cannot read it.
The contract is immutable, so this cannot be fixed at source; it has to be
handled by the reader. We fall back to a regex for that field. Without it, one
work in 1,111 silently has no title and cannot be opened. If your indexer parses
byteGAN metadata strictly, this is the one that will break it.

---

## Where the work lives

| | |
|---|---|
| Artist site | <https://www.vanarman.com> |
| *Reflection* | <https://www.sovrn.art/curated/reflection> |
| — the on-chain account | <https://www.sovrn.art/curated/reflection/on-chain> |
| *byteGANs* | <https://www.sovrn.art/curated/bytegans> |
| *Emerging Faces* | <https://www.vanarman.com/emergence> |
| Raster — Reflection | <https://www.raster.art/artwork/reflection-by-pindar-van-arman> |
| Raster — byteGANs | <https://www.raster.art/artwork/bytegans-by-pindar-van-arman> |
| Raster — Emerging Faces | <https://www.raster.art/artwork/emerging-faces-by-pindar-van-arman> |

All three trade on Raster.

Sovrn also mirrors every work of the three fully on-chain collections — 2,218
files in all, *Reflection*, *Wunderkammer* and *byteGANs* — as static SVG served
from our own origin, decoded from exactly what `tokenURI` returns and otherwise
untouched. If you ever want a rendering source that cannot go dark independently
of your own site, ask and we will point you at it.
