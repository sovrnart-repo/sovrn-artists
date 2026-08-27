# Isa Kost — reference notes

Compiled from sovrn.art, which published *Wunderkammer*. Companion to
**raster.art/artist/isa-kost/about**.

There is an indexing note at the end: this contract does not implement
`ERC721Enumerable`, so it has **no `totalSupply()`**.

---

## The artist

An Italian artist who studied art and graduated in **Architecture**. She came to
blockchain in 2018 through Steemit and the drawing platform **Dada.art**,
collaborating with Dada and its collective from 2019 to 2023.

Her practice is defined by a deep connection with death — a **self-archeology**
in which finding speaks to what is lost. She mixes analog techniques
(printmaking, collage, embroidery) with digital ones, and describes herself as an
explorer setting out to discover new lands or species.

- <https://isakost.net>

---

## The work

| | |
|---|---|
| Title | *Wunderkammer* |
| Released | 14 January 2025 |
| Objects | 108 |
| Chain | Ethereum — fully on-chain |
| Contract | `0x976A8Abe425dc8d7cE7736C54834DbB720695b76` |

An on-chain **Cabinet of Wonders**: 108 objects, each a dead memory or presence
Kost has carried — a ficus leaf, a sun spider, a gardenia — granted permanence
on-chain.

In her words: the journey became clear when, drawing the ficus leaf, the memory
of her father caring for a ficus plant in the family house arose. So did the sun
spider, found through a childhood desire to visit the pyramids in Egypt, and the
scent of the gardenia that enveloped her room in Mexico for days.

Every object is a dead memory and a dead experience that has called out to be
found, and she grants them each eternity with a place on-chain. The approach
threads preservation-as-practice through the history of humanity's relationship
to rare objects, scientific inquiry and the unknown.

*Wunderkammer* is one of the **three fully on-chain Sovrn collections** —
`tokenURI` returns the artwork itself as a base64 SVG, with no gateway and no
IPFS in the path.

---

## Indexing note: there is no totalSupply()

The *Wunderkammer* contract **does not implement `ERC721Enumerable`** — confirmed
via ERC-165. There is no `totalSupply()` to call.

The figure of **108** comes from the collection page, stated by the artist, not
from the chain. Every other Ethereum collection in the Sovrn programme has its
count read directly off the contract; this is the one that cannot be.

If your indexer derives supply by calling `totalSupply()`, this collection will
come back empty or throw rather than returning 108. Token ids are **1-indexed**,
running 1–108.

---

## Provenance

**Francisco Carolinum, Linz — permanent collection.** *Sacred Foot* is one of
eleven works in the Sovrn Full Ethereum Set, and the most recent of them.
Curator Julia Staudach; OÖ Landes-Kultur GmbH.
<https://www.sovrn.art/museums/fransisco-carolinum>

---

## Links

| | |
|---|---|
| Artist site | <https://isakost.net> |
| *Wunderkammer* | <https://www.sovrn.art/curated/wunderkammer> |
| Raster | <https://www.raster.art/artwork/wunderkammer-by-isa-kost> |
