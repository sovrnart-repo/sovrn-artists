# Sovrn artists — reference notes

Eleven artists, fifteen collections. One document each, written to be handed to
someone building a page about the artist — a marketplace, a museum, a writer —
and to save them the research.

Compiled from [sovrn.art](https://www.sovrn.art), which published the work, from
the collection contracts themselves, and from the artists' own submitted
documents. Where a fact is not on sovrn.art, the document says so and gives the
primary source instead.

## The artists

| Artist | Collections | Notes |
|---|---|---|
| [Rutherford Chang](artists/rutherford-chang.md) | CENTS | 1979–2025. The only Bitcoin collection in the programme |
| [Pindar Van Arman](artists/pindar-van-arman.md) | Reflection, byteGANs, Emerging Faces | Co-runs Sovrn; LACMA permanent collection |
| [Anne Spalter](artists/anne-spalter.md) | AI Spaceships, RABBIT TAKEOVER | AI Spaceships was the first Sovrn Curated release |
| [Norman Harman](artists/norman-harman.md) | SIGHTSEERS, Sightseers: Perimeter Town | |
| [Mikey Woodbridge](artists/mikey-woodbridge.md) | Latent Couture | The most institutionally exhibited Sovrn collection |
| [bashobits](artists/bashobits.md) | Seasons of Mobility | |
| [Isa Kost](artists/isa-kost.md) | Wunderkammer | Fully on-chain |
| [Bård Ionson](artists/bard-ionson.md) | Painting with Fire: a history in GANs | |
| [Martin Lukas Ostachowski](artists/martin-lukas-ostachowski.md) | Noctilucent Mementi | Maintains the History of Crypto Art timeline |
| [Look Highward](artists/look-highward.md) | Possibility Spaces | 21K × 12K deep-zoomable works |
| [aleqth / Alex Headlam](artists/aleqth.md) | cope. Vol 1 | A self-published book, tokenised leaf by leaf |

## If you are building a page from these

Each document ends with a links table, and several carry a **handling note** —
something that will otherwise cost you an afternoon. The ones most likely to
matter:

- **Seasons of Mobility is 365 works, not twelve.** The number on our own
  collection page is the display selection, not the edition.
- **Wunderkammer has no `totalSupply()`.** Its contract does not implement
  `ERC721Enumerable`, so an indexer that derives supply that way gets nothing.
  The count is 108, stated by the artist.
- **Do not centre-crop Latent Couture.** It cuts the headpieces off, and the
  headpiece is frequently the whole look.
- **Reflection token ids are zero-based** while the artist's list is 1-based, so
  `id = list number − 1`. Reading a number off a title card and querying it
  directly returns the neighbouring work, with no error to warn you.
- **byteGAN #469's metadata is malformed on-chain** — an unquoted `attributes`
  key that `JSON.parse` cannot read. The contract is immutable, so it has to be
  handled by the reader.
- **Three Raster slugs are not derivable from the title**, and are given in full
  in the relevant documents.

## Press

Each document ends with the press, institutional and further-reading links
sovrn.art carries for that artist. Coverage is uneven and the documents say so
rather than papering over it: Rutherford Chang has around forty links including
Frieze, ARTnews, The Art Newspaper, Monopol and two Chinese outlets, while for
several artists the site carries nothing but their own site.

Every link was checked on 27 August 2026. Four were dead and are **marked in
place rather than removed**, since a reader is better served knowing a source
existed than wondering why it is missing.

One judgement call worth naming: the *GAN Timeline* on the Painting with Fire
page carries roughly 170 outbound citations — arXiv papers, museum pages, other
artists' profiles. Those are the sources of the history Bård Ionson assembled,
not press about him, so his document links the timeline whole instead of listing
them.

## Provenance and corrections

Work counts are `totalSupply()` read from each collection's contract rather than
published claims, except where a document says otherwise and explains why.

Where something is drawn from the artists' submission corpus rather than from
sovrn.art — a few exhibitions and one release date — the document marks it and
links the primary source, so nothing here rests on our word alone.

Quoted material belonging to others is cited and linked rather than reproduced.

Corrections are welcome: open an issue, or write to us through
[sovrn.art](https://www.sovrn.art).
