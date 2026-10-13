# Chog Frequencies — Chog Chemistry

A playful, client-side Chog Genesis sound experience for **anyone**. Tap **Surprise me** to hear an immediate duet from two real Chog tokens. Their verified metadata traits shape their browser-synthesized voices; making music is optional.

## Try the duet

Open `index.html` in a modern browser and tap **Surprise me**. The app chooses a new pair from its six embedded Chog snapshots and starts the duet with one gesture. **Replay pairing** repeats the current pair; **Swap A** or **Swap B** changes one token and plays the new duet. The artwork and metadata snapshots are embedded, so this experience does not need a network lookup.

The **Meet the Chogs** section keeps the layout lighter with four cards at a time: the current pair plus two ready-to-pair sample picks. All six verified snapshots remain available to Surprise me and the A/B swap controls. The current pair is named by token ID and selected real traits. Tier is metadata for context only; it does not boost loudness, quality, or any other musical advantage.

The **Duet Hunt** is a finite, offline listening challenge: explore six embedded sample Chogs, compare a pairing with **Swap A/B**, and collect up to 15 unique unordered sample pairings in **My Duet Book**. The book saves only in the current browser. This is not a daily, shared, or leaderboard retention loop, and it does not claim that every pairing has a unique sound signature. The rhythm studio is optional. Visitors can leave the duet untouched, or adjust tempo, drum level, synthesized kick/clap/shaker lanes, and the editable eight-step Chog voice lanes. Solo audition, the Beat Card, local mix saves, and PNG export remain available.

**Swap A/B** picks from the six embedded samples, so it works instantly without a lookup. For a specific token, expand **Load a specific token ID**; that optional read-only Monad/IPFS lookup needs network access and replaces the selected slot.

## Verified offline sample pool

The starter pair is token IDs **445** and **299**. Four more snapshots are embedded, bringing the pool to six:

| Token ID | Verified metadata name | Example sound-driving traits |
|---|---|---|
| 445 | CHOG #1906 | Aqua background; Royal Blue Aura; Prisoner body; Closed Eye Crying eyes |
| 299 | CHOG #1760 | Lime Green background; Zero THOTS body; Clown Eye eyes; no Aura |
| 664 | CHOG #664 | Sky Blue background; Gangster suit body; Tired eyes |
| 1000 | CHOG #1000 | Red Sky background; Royal Blue Aura; Wizard Cape body; fire laser eyes; Durag |
| 1500 | CHOG #1500 | Lemon Yellow background; Royal Aura; Worried mouth; Dead eyes |
| 1969 | CHOG #1969 | Light Purple background; Banana suit body; normal smile; Side Eye |

The four additions were checked against the Chog Genesis ERC-721 `tokenURI()` metadata on Monad (chain ID 143); their matching IPFS JSON and artwork were checked before being embedded. Marketplace listings were not used as the source of trait data. The collection contract is `0xc96d31F8626c6D03Fae5dCD3d61e3FB9F4a73763` (this is the NFT contract, not the `$CHOG` fungible-token contract).

- [Chog Genesis contract on Monadscan](https://monadscan.com/address/0xc96d31F8626c6D03Fae5dCD3d61e3FB9F4a73763)
- [Token #664](https://opensea.io/item/monad/0xc96d31f8626c6d03fae5dcd3d61e3fb9f4a73763/664) · [#1000](https://opensea.io/item/monad/0xc96d31f8626c6d03fae5dcd3d61e3fb9f4a73763/1000) · [#1500](https://opensea.io/item/monad/0xc96d31f8626c6d03fae5dcd3d61e3fb9f4a73763/1500) · [#1969](https://opensea.io/item/monad/0xc96d31f8626c6d03fae5dcd3d61e3fb9f4a73763/1969)

## How the sound follows the Chog

- **Background** chooses tonal center and scale.
- **Eyes** choose melodic contour, waveform, and default voice pattern.
- **Body** shapes note attack, decay, and gate length; the #1500 sample has no Body trait and uses an explicit neutral envelope.
- **Side** pans the voice slightly left or right.
- **Aura** adds a quiet shimmer accent.
- Every Background, Eyes, and Body value present in the six embedded samples has an explicit mapping. Unfamiliar live-token values still use deterministic fallbacks.
- For read-only live-token lookups, token ID plus Head/Mouth traits can add a subtle phrase signature. Shared links treat live metadata as a snapshot.
- Tier/rarity does not make a voice louder, better, or more powerful.

Pairing two Chogs combines their trait-derived voices. The six embedded samples have explicit mappings for their sample values; deterministic fallbacks for other traits do not guarantee a unique signature for every Chog in the 1,969-token collection.

## Sharing, privacy, and scope

**Share** opens the browser's native share options for the current pair where supported. The adjacent **Copy link** button tries to copy a short pair URL automatically, shows it in the page, and has a manual-copy fallback. For embedded sample pairs, a one-character code identifies the ordered pair; recipients hear the default groove. For custom tempo and step edits, use the Beat Card's **Share beat**, which preserves the full mixer state. Pairings that include a live-looked-up token may need a longer metadata snapshot. This client-side app uses no external shortener or storage. Links are only generated from a public HTTP(S) origin; local addresses and gated sandbox-preview hosts are blocked rather than copied as if they were public links.

**Save mix** stays in this browser and keeps up to eight saved grooves. The separate **Duet Book** stores only embedded sample-pair IDs in this browser; it can be replayed or edited here, but does not sync across devices. There is no account, wallet connection, ownership verification, purchase, transfer, backend, cloud save, or on-chain write. Audio is synthesized in the browser. Optional live lookup reads Monad/IPFS metadata only; it does not sign or submit transactions. The embedded sample pair and artwork work offline.

The full-width musical-note rail remains decorative and independent of playback. It respects reduced-motion preferences. Responsive styling and comfortable touch targets are retained.

## Run or host

This is a static, self-contained HTML/CSS/JavaScript app. Open `index.html`, or serve the project root from any static host. For Vercel, select **Other**, leave the build command empty, and use the repository root. No environment variables, credentials, or build step are required. All six sample artworks and their metadata are embedded in `index.html`.

`chog-frequencies-ui-update.zip` is the refreshed upload bundle and contains the deployable `index.html` at the archive root. The README is maintained separately in the project folder.

## Quick testing instructions

1. Open the app in a modern browser and tap **Surprise me**; confirm a two-Chog duet starts after the gesture.
2. Use **Replay pairing**, **Swap A**, and **Swap B**. The swap controls use the six embedded samples and need no network.
3. In **Duet Hunt**, find a new pair, listen, use **Swap A/B** to compare, then add it to **My Duet Book**. Reload the page to confirm the local book persists; use **Play duet** and **Remove** on a saved entry.
4. Open the optional rhythm studio. Toggle a step with a mouse or keyboard, then change tempo and drum level while playback runs.
5. Use the pairing **Copy link** button and open the copied URL in a fresh tab. For custom tempo or step edits, use Beat Card **Share beat** instead.
6. Try **Save mix** and **Download card**. To test a specific token, expand the optional lookup panel in a regular browser with network access; no wallet is needed.

## Validation status

The project owner manually tested the app in Safari and Firefox. JavaScript syntax and HTML parsing passed. A local logic harness checked the six embedded sample mappings, all 15 unordered sample pairings, and unknown-trait fallbacks.
