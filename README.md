# Chog Frequencies — playable proof of concept

A self-contained browser prototype for the Chogathon concept: **Chog Genesis traits shape distinct musical voices that guests can audition and layer into a chorus.** The two starter cards use authentic token metadata and NFT artwork.

## Run it

Open `index.html` in a modern browser. Click **Hear the chorus** or **Play Chog Groove** to hear the kick, clap, shaker, and Chog voices together. The studio has editable 8-step lanes for each drum and Chog voice, plus tempo and drum-level controls. Click **Listen solo** on a token card to hear that Chog over the beat. All audio is synthesized locally with the Web Audio API.

A fuller, full-width **Frequency Rail** sits directly below the navigation. Musical-note glyphs flow continuously from left to right in the 42px desktop strip. It is purely decorative: no text, BPM, note readout, or playback/pattern connection. Reduced-motion settings freeze the notes; the hero Chog artwork uses layered perspective and hover lighting, while touch pointers do not get the hover-only tilt. Mobile layout QA remains deferred until hosting.

The **Chog Beat Card** is intentionally minimal: Chog pairing, a note/key signature, BPM, and one continuous waveform streak—not the complete step grid or a list of every trait.

- **Save mix** stores the current groove in this browser only. It keeps the latest eight; it does not sync between browsers or devices.
- **Share beat** makes a playable URL. Its URL-safe encoded snapshot restores both Chog voice lanes, all three drum lanes, tempo, drum level, mute states, and the current solo/duo playback selection. A receiver sees shared token/trait metadata as a **snapshot**; the app does not perform a fresh lookup for those Chogs. Live-token phrase signatures are retained in the snapshot.
- **Download card** exports a 1200 × 630 PNG with the Chog artwork (when available), note signature, tempo, and single frequency trace. The share URL still carries the full playable mix.

Saving and sharing are client-side only. There is no account, wallet, backend, or external storage. The playable link works for other people only after the app is hosted on an accessible public origin. Until then, treat it as a local prototype link; the sandbox preview is not a public share URL.

To audition a different Chog, enter its **Chog Genesis ERC-721 token ID** in the lookup panel and choose Slot A or B. The browser makes read-only requests to Monad mainnet (`eth_chainId`, `eth_call` for `tokenURI(uint256)`) and then fetches the referenced IPFS JSON. It verifies chain ID `143`, checks the metadata trait list, and tries Pinata followed by Web3.Storage, IPFS.io, and dweb.link gateways. The request never signs a message or sends a transaction. If a lookup fails, the two existing audition voices remain available.

The in-app HTML preview runs in a network-isolated iframe, so live RPC and IPFS requests may be blocked there. Use a regular browser with network access to try a live lookup; the embedded sample art and traits still work offline.

## Real sample data

- Chog Genesis ERC-721 contract on Monad: `0xc96d31F8626c6D03Fae5dCD3d61e3FB9F4a73763` (distinct from the `$CHOG` fungible-token contract).
- Token ID `445` has metadata name `CHOG #1906`: Aqua background, Royal Blue Aura, Prisoner body, Closed Eye Crying eyes, Common tier.
- Token ID `299` has metadata name `CHOG #1760`: Lime Green background, Zero THOTS body, Clown Eye eyes, Uncommon tier, and no Aura.
- Both `tokenURI()` values and the referenced JSON/art were checked against Monad/IPFS. The snapshots are embedded so the sample experience needs no network access.
- Token references: [#445](https://opensea.io/item/monad/0xc96d31f8626c6d03fae5dcd3d61e3fb9f4a73763/445) · [#299](https://opensea.io/item/monad/0xc96d31f8626c6d03fae5dcd3d61e3fb9f4a73763/299) · [Contract](https://monadscan.com/address/0xc96d31F8626c6D03Fae5dCD3d61e3FB9F4a73763)

## Why the Chog NFT matters

This is not a generic beat-maker with Chog art added on top. Each Chog token's metadata supplies the identity of its musical voice: background sets its tonal palette, eyes shape melody and waveform, body traits shape the envelope, and selected head/mouth traits plus token ID add a phrase signature. Pairing different Chog tokens combines those token-specific voices into a distinct chorus. Remove the Chog metadata and the central paired-voice experience disappears; the editable drums are only its backing.

The dynamic **Trait → Sound** panel makes that dependency visible for the currently loaded A/B slots. It shows each token's computed palette, waveform, envelope, stereo pan, aura accents, and eight-step melody/rest phrase (including the current editable voice pattern), with a solo audition control on each card. Live lookups use token ID plus Head/Mouth traits for a subtle phrase-contour offset; shared snapshots retain that signature when present.

The starter cards use real Chog token snapshots so the demo works offline. Read-only Monad lookup can load another token's metadata; it does not verify the user's ownership or require a wallet.

## Prototype mapping

- A synthesized kick, clap, and shaker provide a syncopated 4/4 pocket on independent, editable step lanes. The drum level is adjustable; no recorded drum samples are loaded.
- Background chooses a tonal center and scale.
- Eyes choose a melodic contour and default step pattern.
- Body shapes the note attack, decay, and gate length within each beat.
- Side pans the voice slightly left or right.
- Aura adds a quiet shimmer accent.
- Other trait values get deterministic fallback mappings, so unfamiliar traits still contribute to a voice.
- A live token's ID, head, and mouth traits add a subtle phrase signature. Tier/rarity does **not** increase volume, quality, or advantage.

## Build status and limitations

The client-side prototype includes editable synthesized drums, a decorative musical-note rail, the dynamic A/B Trait → Sound comparison, a minimal note-and-waveform Beat Card, local-only saves, playable share links, and PNG export. Shared links preserve both Chog voice lanes, all three drum lanes, tempo, drum level, mute states, solo/duo selection, and any live-token phrase signature in the snapshot. Shared metadata is clearly labeled as a snapshot, not a fresh on-chain lookup.

Early feedback from one additional tester was positive, especially about beat-making. This is encouraging qualitative feedback—not evidence of repeat use or retention. The project has not yet had Chog-holder testing.

The app is static HTML/CSS/JavaScript and uses browser-generated audio. It has no build step, backend, account system, wallet connection, ownership verification, cloud save, or on-chain transaction. Live lookup is read-only. The source is **not yet publicly deployed**; add the public Vercel URL to the project submission after deployment. Do not share the gated sandbox preview URL as the demo link.

## Deployment

The app can be deployed as a static site from the repository root. For Vercel, choose **Other** as the framework, leave the build command blank, and serve the root directory; the root `index.html` is the entry page. No environment variables or secrets are required. The sample metadata and artwork are embedded in the HTML; there are no separate runtime assets to build.

## Validation status

The current source passes JavaScript syntax checks, HTML/CSS parsing, and mocked DOM/audio smoke tests. Those are simulated checks, not real-browser listening or live-network tests. Before relying on the demo, test actual playback in a regular browser, try read-only Monad/IPFS lookup on a network that permits it, open a shared link in a second browser, and do the deferred mobile-layout and phone-speaker checks after deployment.
