# Raunak Oberoi

<a href="assets/raunak-portrait-circle.svg"><img align="left" src="assets/raunak-portrait-circle.svg" width="15%" alt="Circular illustrated portrait of Raunak, with birds reflected in blue glasses and a pencil tucked behind his ear. Open the full-size portrait."></a>

Builder of stuff.

**Local AI, speech interfaces, and custom harnesses.**

[LinkedIn](https://www.linkedin.com/in/raunakoberoi/)

<br clear="all">

---

<details>
<summary><img src="assets/shambu-icon.png" width="32" height="32" align="absmiddle" alt=""> &nbsp; <strong>Shambu</strong> &middot; A quiet, whimsical status app for your private GPU server.</summary>

Your GPU is at home, but you need to be out and about. Shambu checks that the two of you are still on speaking terms, with server status, live GPU load, memory usage and 48 hours of activity.

**[Download for Windows, Mac or Android](https://github.com/desigrit/shambu/releases/latest)** &nbsp; / &nbsp; [Repository](https://github.com/desigrit/shambu)

<a href="assets/shambu.png?v=1.0.4">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/shambu-cover-mobile.png?v=1.0.4">
    <img src="assets/shambu-cover.png?v=1.0.4" width="1200" alt="Shambu showing server readiness, live GPU load, VRAM usage and 48 hours of activity. Open the full-size screenshot.">
  </picture>
</a>

**Separate connection checks from server diagnostics**

- **Two paths answer different questions.** I approved one Rust backend and a shared interface for Windows, Mac and Android, but the checks need different sources of evidence. Each client contacts Ollama directly for reachability and model availability. A separate, authenticated host companion reports the GPU PC's Tailscale state, forwarding setup and GPU readings. A phone cannot inspect those server details from its own local network status.

- **I challenged a misleading failure state.** My phone could reach Ollama through the PC's Tailscale address while Shambu showed Tailscale as "Not linked." The route clearly worked; the phone had not been paired for host diagnostics. I pushed back on treating missing diagnostic access like a broken connection. The current wording still needs to distinguish those states more clearly.

- **Readiness checks should not create GPU work.** The companion uses read-only endpoints and fixed system queries. It never loads a model or runs a test prompt. That keeps monitoring from consuming the resource being monitored, but it also limits the claim: reachable services and available models do not establish inference speed or answer quality.

- **GPU activity needs an honest definition.** The 48-hour chart combines GPU utilization with recent evidence that Ollama has a model in GPU memory. A loaded model alone does not count as activity. Other GPU work can still contribute, and short bursts can fall between samples, so the chart is an estimate rather than a request counter. Live readings expire after 15 seconds; missing readings show N/A, while a measured zero stays zero.

[Host companion and evidence sources](https://github.com/desigrit/shambu/blob/main/docs/host-agent.md) · [Status and recovery states](https://github.com/desigrit/shambu/blob/main/docs/ux-states.md)

</details>


<details>
<summary><img src="assets/zebby-icon.png" width="32" height="32" align="absmiddle" alt=""> &nbsp; <strong>Zebby the Scout</strong> &middot; Plan a role, prepare your CV and track what happens next.</summary>

A desktop app for job seekers, with local models, your own API keys or optional Zebby credits.

**[Download for Windows or Mac](https://github.com/desigrit/zebby-the-scout/releases/latest)** &nbsp; / &nbsp; [Repository](https://github.com/desigrit/zebby-the-scout)

<a href="https://github.com/desigrit/zebby-the-scout/blob/main/docs/screenshots/zebby-collage.png">
  <img src="assets/zebby-collage.jpg" width="1200" alt="Zebby's Plan and Applications screens, showing resume matching, ATS keywords and application tracking. Open the full-size image.">
</a>

<sub>Sample applications and analysis results.</sub>

**Scoring, model limits and paid analysis**

- **The 62% versus 90% result made me question the score itself.** Two local models gave those answers for the same resume and role. I wanted the result to separate a requirement's importance from the evidence in the resume, so an essential skill could appear even when the document did not demonstrate it. That comparison exposed inconsistency; it did not establish which model was correct. The score remains a rough guide, not an employer's screening result.

- **The smallest model gets a narrower task.** In SmolLM2 mode, code calculates keyword coverage and the model suggests limited wording edits. It does not judge the depth of someone's experience. I wanted that distinction visible because a keyword score and a full resume assessment answer different questions. More capable models retain the full analysis rather than silently falling back to a simpler score.

- **An unchanged rewrite needs an explanation.** When my summary came back untouched, I asked why. Keeping good wording is a valid result, but silence makes it look like the request failed. The instructions preserve the user's voice and prohibit invented achievements; compact-mode checks can reject an edit and keep the original. Those checks also risk rejecting useful changes, so factual support and writing quality need separate evaluation.

- **I challenged the reservation logic before changing my model choice.** Astra could not start with roughly 90% of my credits still available because the service reserved a large maximum response. I asked to retain my model and thinking level. Quotes now count the complete input and use different output budgets for a match check and a full Plan. Successful runs settle against actual usage and release unused credit. Upfront reservations and response-length limits still matter.

- **Removing signup moved the complexity into recovery.** I chose a guest wallet with device access, a recovery code and temporary pairing codes. Wallet credentials live outside the shared SQLite applications file, so syncing job records does not also share spending access. Checkout is simpler, but losing every paired device and the recovery code prevents automatic recovery.

- **Paid analysis should survive navigation.** I pushed back when leaving a page stopped work and when moving a Plan to Applications would require another analysis. Requests now remain tied to their original job, protect against late results overwriting a changed Plan, and carry the score forward into Applications. That makes cancellation, duplicate requests and the point at which a result is saved part of the product design.

[Full decision notes](https://github.com/desigrit/zebby-the-scout#product-decisions) · [Analysis rules](https://github.com/desigrit/zebby-the-scout/blob/main/desktop/analysis-contracts.ts)

**Analysis options and credits**

- **Bring your own key:** OpenAI or Anthropic, billed to your provider account.
- **Run locally:** use your Ollama server or download a CPU model in Settings.
- **Zebby credits:** buy a pack for online analysis, then choose GPT-6.1 Sol or GPT-6 Astra. No signup or API key needed.

</details>

<details>
<summary><img src="assets/kaptus-icon.png" width="32" height="32" align="absmiddle" alt=""> &nbsp; <strong>Kaptus</strong> &middot; Companion captions for films and television.</summary>

Currently an early Android preview.

**[Download Android preview](https://github.com/desigrit/kaptus/releases/latest/download/Kaptus-preview.apk)** &nbsp; / &nbsp; [Repository](https://github.com/desigrit/kaptus)

<a href="assets/kaptus.png">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/kaptus-cover-mobile.png">
    <img src="assets/kaptus-cover.png" width="1200" alt="Kaptus: companion captions in sync with the scene. Its Wordbird icon sits beside a product mockup of the Android caption player. Open the full-size image.">
  </picture>
</a>

<sub>Android product mockup with illustrative subtitle text.</sub>

**Scene matching without continuous transcription**

- **I narrowed the recognition problem.** The viewer selects a movie or episode, and speech recognition helps locate the current scene in an existing subtitle file. This avoids asking one system to identify an unknown film, generate accurate captions and synchronize them at once. The original subtitle text remains the display source; punctuation and formatting are normalized only for matching.

- **The timing discussion changed my proposed architecture.** I initially suggested a second, near-instant model to synchronize captions after transcription. The better answer was already available in the audio timestamps: match the captured dialogue to a subtitle position, advance that position by the processing time, then let a monotonic clock drive playback. I accepted that approach because a second model would add work to a timing problem the clock could handle.

- **I pushed back on an acquisition flow that took minutes.** I asked to simplify the matching rules and make distinctive word sequences enough to find the scene. The implementation accumulates overlapping dialogue without duplicating words, favors distinctive terms and retains a check for competing matches elsewhere in the film. A latest-only audio queue prevents old windows from building a backlog. Repeated dialogue can still be ambiguous.

- **Listening became an explicit action.** I rejected the microphone restarting when I rotated the phone or manually moved the timeline. Once synchronized, capture stops and the caption clock continues. Opening captions or pressing **Resync** starts recognition. This preserves playback across rotation and app switching, at the cost of asking viewers to resync when the movie pauses, jumps or uses a different cut.

- **Offline use has a distribution cost.** The English model ships inside the roughly 129 MB Android preview, and preparation can save up to three caption tracks. That supports use without a theater connection. I also chose each viewer's own OpenSubtitles key, accepting setup friction and individual download allowances instead of a shared download bill.

[Product decisions and preview limits](https://github.com/desigrit/kaptus#decisions-behind-kaptus) · [Matching, clock and lifecycle checks](https://github.com/desigrit/kaptus/tree/main/app/src/test/java/com/example/kaptus/sync)

</details>

<details>
<summary><img src="assets/rangoli-icon.png" width="32" height="32" align="absmiddle" alt=""> &nbsp; <strong>Rangoli</strong> &middot; Color picker with a live swatch preview for your Mac.</summary>

A menu-bar eyedropper with a live swatch, a nearby color name, and one-click copying in Hex, RGB, HSL, HSV, CMYK, or Lab. Open it with Control-Option-C, pick a pixel, and get back to what you were doing.

**[Download for Mac](https://github.com/desigrit/rangoli-picker/releases/latest/download/Rangoli-macOS-arm64.zip)** &nbsp; / &nbsp; [Repository](https://github.com/desigrit/rangoli-picker)

<a href="assets/rangoli.png">
  <img src="assets/rangoli.png" width="1200" alt="Illustrative desktop mockup of Rangoli sampling a blue pixel, with its format selector above and a live color preview beside the cursor. Open the full-size image.">
</a>

<sub>Illustrative desktop mockup from the Rangoli README, inspired by Audun Rikardsen's Icy Window. Actual picker UI below.</sub>

<p align="center">
  <img src="assets/rangoli-format.png" width="176" alt="Rangoli's compact format selector with Hex selected."> &nbsp;
  <img src="assets/rangoli-preview.png" width="210" alt="Rangoli's live color preview with a swatch, color code, and nearest color name.">
</p>

**Pixel accuracy and a minimal Mac app**

- **I constrained the app to one interaction.** Open the picker, preview a color, copy its code and return to the previous app. I chose native Swift and AppKit, a menu bar entry and a configurable shortcut, with no third-party dependencies. A larger workspace and color history stayed outside the first release. I pushed back when the controls grew too large for that small task.

- **The eyedropper had to copy the pixel it pointed at.** I reported a preview stuck on one color and later a pointer that appeared offset or sampled the background. The sampling path now uses ScreenCaptureKit at native display resolution, includes foreground windows and excludes Rangoli's own panels. It crops one pixel before color conversion, avoiding an average of neighboring pixels. Retina scaling and cursor alignment belong in the accuracy checks, not just visual polish.

- **I reduced the ambition of color naming.** After considering more detailed descriptions, I chose the nearest of the 148 standard CSS color names. This gives a fixed, inspectable mapping and avoids inventing a different description for the same color. It also means a name is approximate. Samples are converted to sRGB; the CMYK option is a screen-color approximation, not a print-profile conversion.

- **Permissions are part of the workflow.** I asked why a tiny picker needed screen-recording access. Reading pixels through the chosen macOS API requires that permission, so capture is limited to active picking and the app provides a retry path. Clicking copies and closes; Esc, right-click and the shortcut cancel. I also pushed back on a cursor that reverted while picking was still active.

[Sampling implementation](https://github.com/desigrit/rangoli-picker/blob/main/Sources/Rang/ScreenSampler.swift) · [Pixel and cursor checks](https://github.com/desigrit/rangoli-picker/blob/main/Sources/Rang/SamplingDiagnostics.swift)

</details>

<details>
<summary><img src="assets/sunno-icon.png" width="32" height="32" align="absmiddle" alt=""> &nbsp; <strong>Sunno</strong> &middot; Live, on-device captions for conversations.</summary>

Speaker labels and native Windows and Mac apps.

**[Download for Windows](https://get.microsoft.com/installer/download/9msv0v6jv8hk?referrer=appbadge&cid=sunno-github)** &nbsp; / &nbsp; **[Download for Mac](https://github.com/desigrit/sunno-macos/releases/latest)** &nbsp; / &nbsp; [Windows source](https://github.com/desigrit/sunno) &nbsp; / &nbsp; [Mac source](https://github.com/desigrit/sunno-macos)

<a href="assets/sunno.png">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/sunno-cover-mobile.png">
    <img src="assets/sunno-cover.png" width="1200" alt="Sunno: live captions on your device. Its Mac interface displays a demo conversation with separate speaker labels. Open the full-size screenshot.">
  </picture>
</a>

<sub>macOS interface with a demo conversation. Select the image for a closer look.</sub>

**Live recognition, corrections and speaker identity**

- **I questioned whether we were using the Mac's hardware well.** The discussion led to processing new audio once where streaming engines allow it, adapting update timing to measured work, and keeping existing engines available for comparison on an M1 Max. For the Mac comparison build, I chose Apple Speech for early captions with optional Whisper large-v3 corrections. Running both costs memory and power, and later corrections can make a line harder to follow even when the words improve.

- **A correction must not block the next sentence.** Live recognition and Whisper correction run in separate workers. At most two corrections can wait, and work older than 12 seconds is skipped. A failed or stale correction leaves the first caption intact; a late result cannot restore cleared text or overwrite a speaker edit. That deliberately gives up some corrections to preserve the live conversation.

- **I challenged speaker labeling as a feature, not just a tuning problem.** A single webinar presenter appeared as several people. The investigation separated speech recognition from the CAM++ voice representations used for speaker matching, so upgrading Whisper alone would not solve it. I rejected a dedicated single-speaker mode because I watch changing video content, and asked for **Off / Automatic (Experimental)** with revisable labels, no confirmation prompts and no required saved voice profiles. Those controls are now in the Windows app; label accuracy still needs evaluation.

- **The Windows confidence formula did not survive the Mac port.** On the same three clips and small model, one mapped score rose from 89 on Windows to 100 on Mac; another rose from 0 to 48. We withheld the Mac clarity badge because the change in scale did not establish better transcription. Three clips could expose the mismatch, but could not calibrate a trustworthy replacement.

- **A hallucination filter also deleted legitimate speech.** A rule meant to catch invented subtitle credits removed "The book was translated by Tolkien himself." Review showed the tests lacked ordinary sentences containing similar words. The filter was narrowed and tests added for both unwanted output and speech that must survive. That is why I want recognition quality judged alongside false deletions, revision frequency and reading effort, rather than a single accuracy number.

[Windows decisions](https://github.com/desigrit/sunno#product-decisions-and-model-judgment) · [Mac correction architecture](https://github.com/desigrit/sunno-macos/blob/main/docs/STREAMING.md) · [Confidence comparison](https://github.com/desigrit/sunno-macos/blob/main/docs/MACOS-PORT.md#the-clarity-score-does-not-transfer-unchanged)

</details>

<details>
<summary><img src="assets/spice-route-icon.png" width="32" height="32" align="absmiddle" alt=""> &nbsp; <strong>Spice Route</strong> &middot; Cross-device continuity for Codex.</summary>

Selected conversations, project files, and Git state move through an existing cloud drive.

**[Download for Windows or Mac](https://github.com/desigrit/project-spice-route/releases/latest)** &nbsp; / &nbsp; [Repository](https://github.com/desigrit/project-spice-route)

<a href="assets/spice-route.png">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/spice-route-cover-mobile.png">
    <img src="assets/spice-route-cover.png" width="1200" alt="Spice Route: your projects across machines. Its native Windows interface shows this computer alongside the latest handoff in the sync folder. Open the full-size screenshot.">
  </picture>
</a>

**Selective sync, version compatibility and recovery**

- **A handoff carries selected records and files.** I wanted full projects, chat history only, and exclusions, using an existing cloud drive. The engine exports selected database records, captures workspace files and Git state, and verifies content hashes before restoring. It does not copy an entire source database over the destination. Device paths and permissions need local handling, while unrelated destination work must survive.

- **I challenged what "latest" could mean.** "This device has the latest handoff" implied more than the app could know. I asked for a comparison between this computer and the handoff visible in its sync folder, plus a reminder to let the drive finish. A successful Push proves local publication; it cannot prove that OneDrive, Google Drive or iCloud has delivered every file to another computer.

- **Duplicate folders exposed two kinds of identity.** After a Pull, I reported empty duplicate projects and asked what would happen to projects created only on the receiving Mac. Codex has both database project IDs and sidebar folder IDs. The fix keeps the destination sidebar identity for a matching project. Equal names are insufficient to merge distinct projects. Conflicting edits are compared against a shared baseline and presented for review.

- **Database compatibility needs more than a version number.** When Codex updates blocked a handoff, I asked for the actual database changes to be inspected. The adapter checks known layouts and preserves supported newer history fields when the destination has no column for them, carrying those values into later handoffs. Unknown layouts still block writes. This avoids silently discarding data, but creates maintenance work as Codex evolves.

- **Recovery is part of the restore design.** Replacing databases, files and Git state cannot happen in one transaction. Pull stages changes and records recovery copies and a journal before applying them. Windows and Mac use different interface shells over the same Rust engine, keeping merge and recovery rules shared. The cost is extra disk use and testing across interrupted transfers, repeated pulls and platform differences.

[Transfer architecture and merge rules](https://github.com/desigrit/project-spice-route/blob/main/docs/architecture.md) · [Database compatibility decisions](https://github.com/desigrit/project-spice-route/blob/main/docs/compatibility-plan.md)

</details>

<details>
<summary><img src="assets/esl-hub-icon.svg" width="32" height="32" align="absmiddle" alt=""> &nbsp; <strong>ESL Hub</strong> &middot; Household dashboards on e-paper displays.</summary>

A Raspberry Pi system that turns retail e-paper displays into household dashboards.

**[Download source](https://github.com/desigrit/esl-home-hub/archive/refs/heads/main.zip)** &nbsp; / &nbsp; [Raspberry Pi setup](https://github.com/desigrit/esl-home-hub#setup) &nbsp; / &nbsp; [Repository](https://github.com/desigrit/esl-home-hub)

<p align="center">
  <a href="assets/esl-hub-tags.jpg">
    <img src="assets/esl-hub-tags.jpg" width="560" alt="Four ESL Hub e-paper tags on a wall, displaying Dota progress, weather, fitness, and home energy dashboards. Open the full-size photo.">
  </a>
</p>

**Delivery confirmation and failure isolation**

- **I wanted status to describe what reached the wall.** Missed updates led to a wider reliability investigation. We found that an accepted gateway request could be reported as success without confirmed delivery to a tag. Publishing now checks the response and polls the gateway's task ID. **Success** means confirmed delivery; **Pending** means accepted but unconfirmed. This adds a wait, but makes the status useful for deciding whether to retry.

- **One integration should not hold up the others.** Controllers run in separate processes with a five-minute deadline, and overlapping runs of the same controller are suppressed. Settings and logs use locked, atomic writes. The investigation also found that reusing whole-second timestamps as task IDs caused collisions between updates; the gateway now assigns them. These choices address failure isolation and concurrency, not just whether an API call returns.

- **I pushed back on changing the wrong layer.** When calendar titles overflowed, I stopped edits to the vendor's Layout Designer and asked for a controller change. We used a title that fit as a 29-character baseline, truncating longer text to 27 characters plus two dots. The controller owns the content; the vendor tool owns the layout. The compromise is that a character budget cannot account perfectly for different letter widths.

- **I challenged the first explanation for missing events.** The initial answer focused on the display's four-row limit. I knew expected events were absent and asked which calendar was being read. The follow-up found that events without accessible titles were filtered out before reaching the layout. That changed the diagnosis from limited screen space to permissions and data handling.

- **I chose to pause unavailable feeds.** When two upstream integrations stopped working, I asked to pause them instead of repeatedly retrying. Their configuration remained available for later use, and failed fetches preserve the last display. For e-paper that is a deliberate compromise: a readable old value can remain on the wall, so successful delivery and fresh, complete information must be judged separately.

[Reliability behavior and diagnosis](https://github.com/desigrit/esl-home-hub#run-reliability-and-diagnosis) · [Regression checks](https://github.com/desigrit/esl-home-hub/blob/main/tests/test_robustness.py)

</details>
