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
<https://www.ooekultur.at/en/exhibitions-events/art-of-punk> — **note this
  page has since been taken down** (404 as of 27 August 2026); the museum itself
  is at <https://www.ooekultur.at/en/location-detail/francisco-carolinum-linz>

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
| bitGANs | <https://bitgans.com/> |
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

## Press and institutional links

Everything sovrn.art links for Van Arman.

- LACMA — *New Acquisition: Cozomo de' Medici Collection*, the museum's own post on the gift — <https://unframed.lacma.org/2023/02/24/new-acquisition-cozomo-de-medici-collection>
- LACMA — <https://www.lacma.org>
- Museum of Crypto Art — the permanent collection — <https://museumofcryptoart.com/collections/the-permanent-collection>
- Museum of Crypto Art — <https://museumofcryptoart.com/>
- Christie's — *Augmented Intelligence*. **The link sovrn.art carries for this
  no longer resolves** (christies.com returns a 404 as of 27 August 2026) and we
  have not found a replacement — an `augmented-intelligence` auction URL still on
  christies.com turns out to be a different sale entirely. The exhibition is real:
  *Emerging Faces* appears in our records as "New York, Augmented Intelligence
  group auction, 2025". Treat the event as sourced, the link as broken.
- byteGANs on SuperRare — <https://superrare.com/vanarman>
- bitGANs — the collective the byteGANs grew out of — <https://bitgans.com/>
- *Emerging Faces* on the artist's site — <https://www.vanarman.com/emergence>
- Lumen Prize 2025, Still Image finalist — <https://lumenprize.org/2025-still-image-finalists/pindar-van-arman>
- ART OF PUNK, OÖ Landes-Kultur — <https://www.ooekultur.at/en/exhibitions-events/art-of-punk> — **note this
  page has since been taken down** (404 as of 27 August 2026); the museum itself
  is at <https://www.ooekultur.at/en/location-detail/francisco-carolinum-linz>

## From the artist's own press page

Everything listed at <https://www.vanarman.com/press>, in the artist's own
two groupings. A handful overlap with the section above and are kept here so
each list stands on its own.

A note on the checking: every link here was tried on 27 August 2026. **17 did not
resolve** and are marked in place rather than dropped — several are 2015–2018
coverage on sites that have since folded or restructured, and two are on
cloudpainter.com itself. Links that answered 403 or 429 are *not* marked: those
are paywalls and bot walls, which look identical to a dead link from outside a
browser and are usually perfectly live in one.

### Exhibitions and awards

- Lumen Prize Finalist — <https://lumenprize.org/2025-still-image-finalists/pindar-van-arman>  *(also above)*
- Augmented Intelligence — <https://www.christies.com/stories/what-is-ai-art-augmented-intelligence-36dc0897d3584268b5102468a3bf8a8c>
- Robotic Artist in Residence at Cook Children's Medical Center — <https://cookchildrens.org/neurology/advanced-technology/Pages/robot-art.aspx>  *(did not resolve, 27 Aug 2026)*
- Sotheby’s Natively Digital 1.3 — <https://www.sothebys.com/en/buy/auction/2022/natively-digital-1-3-generative-art/quantum-skull>
- NVIDIA AI Art Gallery — <https://www.nvidia.com/en-us/gtc/ai-art-gallery/artists/?artist=artist-7-pindar-van-arman>
- SuperRare Monolith — <https://bitgans.com/news/the-podgan-invasion>
- NVIDIA AI ART GALLERY — <https://www.nvidia.com/en-us/research/ai-art-gallery/artists/pindar-van-arman/>
- NeurIPS AI Art Gallery 2020 — <http://www.aiartonline.com/category/highlights/>  *(did not resolve, 27 Aug 2026)*
- Art(ificial) Intelligence — <https://blogs.nvidia.com/blog/2020/10/08/ai-art-pindar-van-arman/>
- Machine, The Art of intelligence — <https://youtu.be/Yp-SrCm3tIQ>
- NeurIPS AI Art Gallery — <https://www.aiartonline.com/art/pindar-van-arman-2/>  *(did not resolve, 27 Aug 2026)*
- NeurIPS AI Art Gallery 2018 — <http://www.aiartonline.com/>  *(did not resolve, 27 Aug 2026)*
- Tysons: Then and Now — <http://vivatysons.com/blog/2018/09/01/worlds-most-advanced-painting-robots-will-join-in-the-celebration-of-tysons-corner-centers-50th-anniversary-this-september/>
- RobotArt 2018 — <http://robotart.org>
- ART.IFICIAL — <https://gumgum.com/artificial-creativity>
- Aspen AI Conference — <https://www.cloudpainter.com/blog/2018/3/20/aspen-institute-ai-conference-recap>  *(did not resolve, 27 Aug 2026)*
- MBN Y Forum 2018 — <http://www.cloudpainter.com/blog/2018/3/8/talking-artificial-creativity-in-korea>  *(did not resolve, 27 Aug 2026)*
- DC DataCon 2017 — <http://www.ncsi.com/dcdatacon/2017/agenda.php>  *(did not resolve, 27 Aug 2026)*
- IROS 2017 — <http://www.roboticart.org/iros2017/>  *(did not resolve, 27 Aug 2026)*
- NVIDIA GTC 2017 — <https://www.youtube.com/watch?v=SUNPrR4o5ZA>
- CISR 2017 — <http://www.cisr.ornl.gov/cisrc17/speakers/>  *(did not resolve, 27 Aug 2026)*
- Elastic Cause Award — <https://www.elastic.co/causeawards>
- Microsoft Surface Innov8r — <https://vimeo.com/199327259>
- TEDx Talk — <https://www.youtube.com/watch?v=YYu0PdJSZcA>
- RobotArt 2016 — <http://robotart.org/>
- cloudpainter.com — <http://cloudpainter.com/>
- Barbican's Dev Art Competition — <https://devart.withgoogle.com/#/project/17830303?t=shortlisted>

### Press and media

- Inside the Studio with an AI Painting Robot — <https://time.com/6256108/artificial-intelligence-artist/>
- documentary — <https://youtu.be/OJcP4XxXhQ4>
- What is AI Art? — <https://www.christies.com/en/stories/what-is-ai-art-augmented-intelligence-36dc0897d3584268b5102468a3bf8a8c>
- Last Look: Can Robots Make Art? — <https://www.cnn.com/videos/tv/2018/11/19/exp-gps-1118-last-look-gum-gum-robot-painting-pindar-van-arman.cnn>
- The da Vinci Coder — <https://video.vice.com/en_us/embed/5983770a579816cf014bbddf>  *(did not resolve, 27 Aug 2026)*
- You Can Give A Robot A Paintbrush, But Does It Create Art? — <http://www.npr.org/sections/alltechconsidered/2015/12/06/458347976/you-can-give-a-robot-a-paintbrush-but-does-it-create-art>
- Can AIs Create True Art? — <https://blogs.scientificamerican.com/observations/can-ais-create-true-art/>
- How does AI Art Stack Up Against Human Art — <https://news.vice.com/en_us/article/ywqw8j/how-does-ai-art-stack-up-against-human-art>  *(did not resolve, 27 Aug 2026)*
- EP 101 The Dance — <https://cnam.com/project/confluence/101>
- Jerry Saltz Reviewing Art Made by Artificial Intelligence — <https://news.artnet.com/art-world/jerry-saltz-ai-art-1227932>
- AI Painting Robot — <https://news.developer.nvidia.com/ai-painting-robot/?_lrsc=ccad5385-3afb-49e9-b0af-272b3476b95d&amp;ncid=so-twi-lt-799>
- Is A.I. Helping or Hindering the Creative Industries? — <https://cnb.cx/2BEUgFR>
- Can Artificial Intelligence Create Art — <https://youtu.be/ii9qyjrhgcY?t=1120>
- Digital Art Stars and Tech Pioneers Lead Christie’s First All-A.I. Sale — <https://news.artnet.com/market/christies-augmented-intelligence-ai-sale-2606370>
- AI-powered robot, helps patients at Cook Children’s make art — <https://www.keranews.org/arts-culture/2023-09-21/spikelangelo-an-ai-powered-robot-helps-patients-at-cook-childrens-make-art>
- Art of AI and Machine — <https://podcasts.apple.com/au/podcast/art-of-ai-and-machine/id1330288427?i=1000460918206>
- Recreating Paintings with AI and 3D Printing — <https://www.forbes.com/sites/charlestowersclark/2018/11/30/recreating-paintings-with-ai-and-3d-printing/>
- First Christie’s Auction Devoted to AI Art Sparks Backlash — <https://www.forbes.com/sites/lesliekatz/2025/02/09/christies-to-hold-first-auction-devoted-solely-to-ai-art-amid-pushback/>
- Why automation won’t put artists out of work just yet — <https://www.pbs.org/newshour/arts/why-automation-wont-put-artists-out-of-work-just-yet>
- AI at Christie’s: auction scandal — <https://magazine.luxus-plus.com/en/ai-at-christies-auction-scandal/>
- Five Robots that can Paint Like Humans — <https://roboticsandautomationnews.com/2025/05/06/five-robotic-systems-that-can-paint-like-human-artists/90362/>
- Christie’s to host groundbreaking auction featuring only AI Art — <https://www.msn.com/en-us/news/us/christie-s-to-host-groundbreaking-auction-featuring-only-ai-art/ar-AA1yNMpA?apiversion=v2&amp;noservercache=1&amp;domshim=1&amp;renderwebcomponents=1&amp;wcseo=1&amp;batchservertelemetry=1&amp;noservertelemetry=1>
- AI Art Auction Angers some Artists — <https://www.straitstimes.com/life/arts/christies-first-ever-ai-sale-angers-some-artists>
- Artificial Intelligence: The New Artistic Revolution — <https://www.artuk.org/discover/stories/artificial-intelligence-the-new-artistic-revolution>
- Can You Guess Which of these Paintings Was Not Made by an Artist? — <https://qz-com.cdn.ampproject.org/c/s/qz.com/work/1390121/can-you-guess-which-of-these-paintings-was-not-made-by-a-human/amp/>
- 用 AI 画画的艺术家目的何在，以及，这些画到底是不是艺术？ — <http://www.qdaily.com/articles/55935.html>  *(did not resolve, 27 Aug 2026)*
- The Robot in Your Studio — <http://www.professionalartistmag.com/shop/print-issues/octobernovember-2016-print/>  *(did not resolve, 27 Aug 2026)*
- This is What Robotic Art Looks Like in 2018 — <https://www.smithsonianmag.com/smart-news/this-what-robotic-art-2018-180969656/>
- Robots That Paint Have Gotten Real Impressive — <https://www.technologyreview.com/the-download/611658/robots-that-paint-have-gotten-pretty-impressive/>
- These Robots are Learning to Become Artists — <https://mashable.com/video/robot-painter-can-arman/#sJLLUrnpokq6>
- Winners of the Robot Art 2018 Contest Swap Pixels for Paintbrushes — <https://newatlas.com/robot-art-2018-competition-winners-gallery/55548/>
- A Glimpse Into The Uncanny World of Robot-Made Fine Art — <https://www.fastcompany.com/90203123/a-glimpse-into-the-uncanny-world-of-art-made-by-robots>
- Robots Made These Paintings and They are Very, Very Good — <https://www.popularmechanics.com/technology/robots/a22148161/robots-made-paintings-theyre-very-good/>
- Artistic Robot that Will Paint Your Portrait Like an Old Master — <https://news.artnet.com/art-world/artistic-robot-paints-portraits-355982>
- Think Technology Has No Place in Art? Think Again. — <https://www.forbes.com/sites/capitalone/2017/12/15/think-technology-has-no-place-in-art-think-again/#265891d262a9>
- These are the Best Robot Painters in the World — <https://www.businessinsider.co.za/robo-picasso-robot-art-competition-2018-7>
- Robots nab $100000 in art competition while human artists continue to starve — <https://www.google.com/url?rct=j&amp;sa=t&amp;url=https://roboticsandautomationnews.com/2018/07/24/robots-nab-100000-in-art-competition-while-human-artists-continue-to-starve/18447/&amp;ct=ga&amp;cd=CAEYAioUMTUyMzg4MTIwMzc4NjIwOTA2MzUyGmYxZjNkNTBlNjJhODY3NTA6Y29tOmVuOlVT&amp;usg=AFQjCNF8io3ZmFkwi-lRVutQsfTXBN1kMA>
- AI Assisted Art Moves From Pixels to Paintbrushes — <https://venturebeat.com/2018/07/20/ai-assisted-art-moves-from-pixels-to-paintbrushes/>
- Paintings By Robots Revealed and They Are Actually Really Good — <https://www.thesun.co.uk/tech/6802263/paintings-by-robots-revealed-and-theyre-actually-really-good/>
- Robot Artists Make a Fine Impression — <https://www.thetimes.co.uk/article/robot-artists-make-a-fine-impression-lhrn7dx88>
- Robots Made These Incredible Works of Fine Art — <https://futurism.com/contest-creative-robots-fine-art/>
- Meet the Machine That Paints Like a High-Tech Picasso — <https://youtu.be/7zgtkJEwaCs>
- Watch These Robots Create Works of Art — <https://cosmosmagazine.com/technology/watch-these-robots-create-works-art>
- This Robot Wants to Paint Your Portrait—With or Without You — <http://thecreatorsproject.vice.com/blog/this-robot-wants-to-paint-your-portrait>  *(did not resolve, 27 Aug 2026)*
- This Virginia Artist Paints With Acrylics, And A Robot — <http://dcist.com/2015/11/this_virginia_painter_has_an_unusua.php#photo-1>  *(did not resolve, 27 Aug 2026)*
- Art in the Age of Ones and Zeros — <http://newatlas.com/art-ones-and-zeros-robotart-painting/49538/>
- A New Bot-ticelli? Robot Painters Show Off Works at Competition — <http://www.livescience.com/54794-robot-art-contest-winners.html>
- Robot Uses Artificial Intelligence to Make Portraits — <http://www.cbsnews.com/videos/robot-uses-artificial-intelligence-to-make-portraits/>
- Watch a Robot Paint Incredible Pieces of Art — <http://www.techinsider.io/pindar-van-armans-robot-can-paint-2016-2>
- This Robot Can Make a Masterpiece of Einstein — <http://www.fromthegrapevine.com/arts/robot-paint-masterpiece-einstein-bitpaintr-pindar>
- Art In a Technological World — <https://edgylabs.com/art-in-a-technological-world>
- Portraits by bitPaintr — <http://www.wusa9.com/videos/entertainment/television/programs/great-day-washington/2015/12/02/portraits-by-bitpaintr/76661644/>
- bitPaintr — <http://www.discovery.ca/dailyplanet>
- A Portrait Painting Robot with Its Own Artistic Style — <http://hyperallergic.com/259625/a-portrait-painting-robot-with-its-own-artistic-style/>
- bitPaintr: A Portrait Painting Robot with a Whole Lot of Heart — <http://beautifuldecay.com/2016/01/08/bitpaintr-portrait-painting-robot-whole-lot-heart/>
- Portrait-Painting A.I. Uses Brush and Canvas — <http://news.discovery.com/tech/robotics/portrait-painting-ai-uses-brush-and-canvas-151101.htm>
- CloudPainter The Robot Artist — <https://www.thequint.com/videos/news-videos/cloudpainter-the-robot-artist>
- This Robot will Turn your Selfies into Painted Portraits — <http://www.sfgate.com/business/article/This-robot-will-turn-your-selfies-into-painted-6613048.php>
- How a Cyber Attack Became Art — <http://www.techtimes.com/articles/33959/20150219/how-a-cyber-attack-became-art.htm>
- You're Fired — <http://fineartamerica.com/showmessages.php?messageid=2780279>
- 8 Innovators Who Are Changing The Art World — <https://www.thrillist.com/lifestyle/nation/innovators-who-are-changing-the-art-world>
- Fancy Having Your Portrait Done by a Robot — <http://nudemolemagazine.com/fancy-having-your-portrait-done-by-a-robot/>  *(did not resolve, 27 Aug 2026)*
- bitPaintr Robot Relies on AI To Complete Portraits — <http://www.ubergizmo.com/2015/10/bitpaintr-robot-ai-portraits/>
- Corcoran Alumnus' Robot Turns your Selfie into Art — <http://www.gwhatchet.com/2015/11/02/for-corcoran-alumnus-a-picture-is-worth-1000-gears/>
- Ist das Kunst? — <http://www.golem.de/news/programmcode-ist-das-kunst-1407-107871.html>
- Paintbots Kick Art to the Curb — <http://www.roundmagazine.net/techniche/730-paintbots-kick-art-to-the-curb>  *(did not resolve, 27 Aug 2026)*
- bitPaintr- A Painting Robot by PindarVanArman — <http://www.creativeai.net/posts/Xux7GJ6BNRY36PRPC/bitpaintr-a-painting-robot-by-pindar-van-arman>
- Talented Engineer Invents Real Life Art2-D2 — <http://www.mirror.co.uk/news/world-news/talented-engineer-invents-real-life-7247872>
- It's ART2-D2 Engineer Designs Robot to Paint with Stunning Precision — <http://www.dailymail.co.uk/news/article-3417282/It-s-ART2-D2-Engineer-designs-robot-precision-PAINT-stunning-masterpieces-using-mechanical-arm-draw-canvas.html>
- This Robot Will Paint your Portrait — <http://www.pddnet.com/news/2015/11/robot-will-paint-your-portrait>
- A Robot Will Paint Your Next Portrait — <https://www.bisnow.com/washington-dc/news/tech/a-robot-will-paint-your-next-painting-51769?rt=title>
- Vincent van Bot: the robots turning their hands to art — <http://www.theguardian.com/artanddesign/2016/apr/19/robot-art-competition-e-david-cloudpainter-bitpaintr>
- See the Impressionist and Self-Portrait Paintings of the First RobotArt Contest — <https://www.inverse.com/article/14531-see-the-impressionist-and-self-portrait-paintings-of-the-first-robotart-contest>
- Second Year of Robot Art Contest — <http://www.roboticmagazine.com/events/second-year-robotic-art-contest>
- The Worlds Next Great Artist Might Be a Robot — <http://thenextweb.com/insider/2016/04/22/worlds-next-great-artist-might-robot/#gref>
