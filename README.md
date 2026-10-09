<a href="assets/raunak-portrait-circle.svg"><img align="right" src="assets/raunak-portrait-circle.svg" width="24%" alt="Circular illustrated portrait of Raunak, with birds reflected in blue glasses and a pencil tucked behind his ear. Open the full-size portrait."></a>

# Raunak Oberoi

**Local AI, speech interfaces, and tools for building.**

I build apps around problems I run into: following conversations, moving between machines, and finding a better way through an everyday task. I take them through the whole stack, from model selection and benchmarks to native interfaces, packaging, and recovery when something breaks.

<br clear="right">

## Projects

### <img src="assets/zebby-icon.png" width="40" height="40" alt=""> &nbsp; [Zebby](https://github.com/desigrit/zebby-the-scout)

**A desktop workspace for role planning and application tracking.** History, documents, and the reasoning for each application in one place.

<a href="assets/zebby.png">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/zebby-cover-mobile.png">
    <img src="assets/zebby-cover.png" width="1200" alt="Zebby: a workspace for your next move. The desktop interface shows sample applications and the selected role's details. Open the full-size screenshot.">
  </picture>
</a>

<sub>Sample application data.</sub>

[Repository](https://github.com/desigrit/zebby-the-scout)

<details>
<summary>Inside the build: local storage and a choice of models</summary>

Application data lives in a local SQLite database; people can choose local or hosted models for analysis.

</details>

<br>

### <img src="assets/kaptus-icon.png" width="40" height="40" alt=""> &nbsp; [Kaptus](https://github.com/desigrit/kaptus)

**Companion captions for films and television.** Currently an early Android preview.

<a href="assets/kaptus.png">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/kaptus-cover-mobile.png">
    <img src="assets/kaptus-cover.png" width="1200" alt="Kaptus: companion captions in sync with the scene. Its Wordbird icon sits beside a product mockup of the Android caption player. Open the full-size image.">
  </picture>
</a>

<sub>Android product mockup with illustrative subtitle text.</sub>

[Repository](https://github.com/desigrit/kaptus)

<details>
<summary>Inside the build: listen, synchronize, then switch the microphone off</summary>

On-device speech recognition locates the current scene in an existing subtitle track. Once synchronized, the microphone stops and a local clock advances the captions.

</details>

<br>

### <img src="assets/rangoli-icon.png" width="40" height="40" alt=""> &nbsp; [Rangoli](https://github.com/desigrit/rangoli-picker)

A native Mac color picker, built with Swift and AppKit.

<br>

### <img src="assets/sunno-icon.png" width="40" height="40" alt=""> &nbsp; [Sunno](https://github.com/desigrit/sunno)

**Live, on-device captions for conversations.** Speaker labels and native Windows and Mac apps.

<a href="assets/sunno.png">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/sunno-cover-mobile.png">
    <img src="assets/sunno-cover.png" width="1200" alt="Sunno: live captions on your device. Its Mac interface displays a demo conversation with separate speaker labels. Open the full-size screenshot.">
  </picture>
</a>

<sub>macOS interface with a demo conversation. Select the image for a closer look.</sub>

[Windows](https://github.com/desigrit/sunno) &nbsp; / &nbsp; [macOS](https://github.com/desigrit/sunno-macos) &nbsp; / &nbsp; [Engineering decisions](https://github.com/desigrit/sunno/blob/master/docs/ENGINEERING.md)

<details>
<summary>Inside the build: accuracy, latency, and readable captions</summary>

I've worked through the trade-offs between accented-speech accuracy, inference latency, and readable captions. The Whisper pipeline uses provisional and final decoding to deliver early captions while limiting disruptive corrections.

</details>

<br>

### <img src="assets/spice-route-icon.png" width="40" height="40" alt=""> &nbsp; [Spice Route](https://github.com/desigrit/project-spice-route)

**Cross-device continuity for Codex.** Selected conversations, project files, and Git state move through an existing cloud drive.

<a href="assets/spice-route.png">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/spice-route-cover-mobile.png">
    <img src="assets/spice-route-cover.png" width="1200" alt="Spice Route: your projects across machines. Its native Windows interface shows this computer alongside the latest handoff in the sync folder. Open the full-size screenshot.">
  </picture>
</a>

[Repository](https://github.com/desigrit/project-spice-route) &nbsp; / &nbsp; [Architecture](https://github.com/desigrit/project-spice-route/blob/main/docs/architecture.md)

<details>
<summary>Inside the build: snapshots, conflicts, and recoverable restores</summary>

A shared Rust engine handles schema compatibility, content-addressed snapshots, three-way comparisons, and recoverable restores. The difficult part is preserving working state when both machines have changed.

</details>

<br>

### <img src="assets/esl-hub-icon.svg" width="40" height="40" alt=""> &nbsp; [ESL Hub](https://github.com/desigrit/esl-home-hub)

A Raspberry Pi system that turns retail e-paper displays into household dashboards.

<p align="center">
  <a href="assets/esl-hub-tags.jpg">
    <img src="assets/esl-hub-tags.jpg" width="560" alt="Four ESL Hub e-paper tags on a wall, displaying Dota progress, weather, fitness, and home energy dashboards. Open the full-size photo.">
  </a>
</p>

[Repository](https://github.com/desigrit/esl-home-hub)

## Field notes

I keep the reasoning alongside the code, including the measurements and the decisions they changed.

**Measure the actual pipeline.** In one recorded Sunno GPU benchmark, FP16 took 322 ms for greedy decoding versus 374 ms for INT8/FP16. Quantization added overhead on that setup. The result mattered more than the expected advantage of a smaller representation. [Measurements and model choices](https://github.com/desigrit/sunno/blob/master/docs/ENGINEERING.md#why-these-choices).

**Design the recovery path.** Spice Route verifies transferred objects before publishing a handoff manifest. Before a Pull changes local state, it creates a recovery set. Handling interrupted transfers and conflicting edits is part of the design from the start. [Transfer and recovery architecture](https://github.com/desigrit/project-spice-route/blob/main/docs/architecture.md).

[LinkedIn](https://www.linkedin.com/in/raunakoberoi/)
