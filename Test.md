<!-- {"achilles-ide-document":{"id":"doc-a95e8615-e53f-4654-a301-8642ca489e7e","updatedAt":"2026-09-03T07:23:34.484Z"}} -->
<!-- {"achilles-ide-chapter":{"id":"chapter-d1b9c2cc-d2e6-4367-bb02-bc3ce814f93f","title":"AchillesIDE","anchorId":"chapter-chapter-d1b9c2cc-d2e6-4367-bb02-bc3ce814f93f"}} -->
<a id="chapter-chapter-d1b9c2cc-d2e6-4367-bb02-bc3ce814f93f"></a>
# AchillesIDE
<!-- {"achilles-ide-paragraph":{"id":"paragraph-974b810d-c324-420e-88e8-f5279167ea8b","type":"markdown"}} -->


<!-- {"achilles-ide-chapter":{"id":"chapter-1328239a-52dd-489e-a80a-71fe8fc698bf","title":"Prerequisites","anchorId":"chapter-chapter-1328239a-52dd-489e-a80a-71fe8fc698bf"}} -->
<a id="chapter-chapter-1328239a-52dd-489e-a80a-71fe8fc698bf"></a>
## Prerequisites
<!-- {"achilles-ide-paragraph":{"id":"paragraph-e82a6799-5755-457d-8d2a-9bcba61872c6","type":"markdown","commands":"@media_image_080ce8 attach id 58a97b871a9591b0dee80dd8fe7bccfe693a64e2b71a456a name \"ChatGPT Image Jun 25, 2026, 04_05_57 PM.png\" width 1254 height 1254 size 1953594\n@media_audio_c199c8 attach id a9e95323d98ca96e6844e6cd6b07507aee4324fcba959c5a name \"Kuntry Boy - Anno Domini Beats.mp3\" volume 50 duration 197.837823 loop false start 0 end 197.837823\n@media_image_90c51e attach id 0d7f0c8cede6599b8b93713b02ad280368d5506d0b1056de name abHNnzqXPAGMis0zci9Q--0--Pa3Qm.jpg width 768 height 1344 size 141157\n@ffmpeg_media_wuk8t1c ffmpegImageToVideo images [createJsonArray \"58a97b871a9591b0dee80dd8fe7bccfe693a64e2b71a456a\" \"0d7f0c8cede6599b8b93713b02ad280368d5506d0b1056de\"] audios [createJsonArray \"a9e95323d98ca96e6844e6cd6b07507aee4324fcba959c5a\"] duration 20 fps 30 width 1280 height 720 bg black","title":"Paragraph 1"}} -->
- Node.js 20 or later.
- The `ploinky` command-line tool.
- A container runtime supported by Ploinky, such as Podman or Docker.


<!-- {"achilles-ide-chapter":{"id":"chapter-83c4bc00-0382-41f6-a007-0a4c49b3f52a","title":"Start Explorer","anchorId":"chapter-chapter-83c4bc00-0382-41f6-a007-0a4c49b3f52a"}} -->
<a id="chapter-chapter-83c4bc00-0382-41f6-a007-0a4c49b3f52a"></a>
## Start Explorer
<!-- {"achilles-ide-paragraph":{"id":"paragraph-26d782fb-c9af-4a9c-9075-c1b6db15630a"}} -->
From a Ploinky workspace that contains this repository, run:

```bash
ploinky start explorer
```

Open the Ploinky dashboard at `http://127.0.0.1:8080/dashboard`, then open Explorer at `http://127.0.0.1:8080/#file-exp/`.

Ploinky starts the dependencies declared in `explorer/manifest.json`, configures the router, and serves Explorer as the workspace's static application. Check the local runtime with:

```bash
ploinky status
curl -I http://127.0.0.1:8080/dashboard
```


<!-- {"achilles-ide-chapter":{"id":"chapter-5825c5c9-92c7-4fc0-b21e-86b290a0738d","title":"Use Explorer","anchorId":"chapter-chapter-5825c5c9-92c7-4fc0-b21e-86b290a0738d"}} -->
<a id="chapter-chapter-5825c5c9-92c7-4fc0-b21e-86b290a0738d"></a>
## Use Explorer
<!-- {"achilles-ide-paragraph":{"id":"paragraph-c55ccf83-5a1d-43ce-a8ea-df3311a688d8"}} -->
Use Explorer to browse workspace files and virtual DPU resources. Normal Markdown uses source editing by default. Select Advanced edit only when the document requires SOPLang-aware structure such as metadata, commands, variables, or references.

Confidential resources appear below `/Confidential`. Explorer displays these resources but delegates storage, permissions, secrets, research-data operations, audit, and provenance to dpuAgent. Configure DPU sources from the administrative Data Sources settings surface; source configurations reference a DPU secret and do not expose its value.

Repository documentation is available through the mounted path `/.ploinky/repos/AchillesIDE/docs/development.html` in a running workspace.


<!-- {"achilles-ide-chapter":{"id":"chapter-63fa9988-cd21-4feb-af97-4bfc8f054bae","title":"Development and verification","anchorId":"chapter-chapter-63fa9988-cd21-4feb-af97-4bfc8f054bae"}} -->
<a id="chapter-chapter-63fa9988-cd21-4feb-af97-4bfc8f054bae"></a>
## Development and verification
<!-- {"achilles-ide-paragraph":{"id":"paragraph-6229902e-ffae-4b7b-920c-855beb5dfa7d"}} -->
Run the affected agent's tests before making a wider change:

```bash
cd explorer && npm test
cd ../dpuAgent && npm test
```

Read the [documentation entry point](docs/index.html), the [terminology wiki](docs/wiki.html), and the [specification matrix](docs/specsLoader.html?spec=matrix.md) before changing a documented behavior. `docs/specs/` contains the normative contracts.

