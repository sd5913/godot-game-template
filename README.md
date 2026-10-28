# Catch the Light: Godot game starter

A tiny 2D GDScript game: move with arrow keys or click/tap to collect the
light. Use **Use this template** to create your team's repository, then change
one rule, visual or sound and ask a teammate to try it.

## Run and export

Open `project.godot` with **Godot 4.5.1** (standard editor, not .NET). Press F6
or Run Project. The starter uses the Compatibility renderer and single-threaded
Web export. Install the **matching 4.5.1 export templates** in the editor for
exports. On a Linux x86_64 cloud runner, `.codex/setup.sh` downloads official
editor and templates and performs headless import. It requires `curl` and
`unzip`, internet and several GB of space; the template archive is large.

```bash
.codex/setup.sh
GODOT="$HOME/.cache/sd5913-godot-4.5.1/godot"
mkdir -p build/web build/linux build/windows && touch build/.gdignore
"$GODOT" --headless --path . --export-release Web build/web/index.html
"$GODOT" --headless --path . --export-release Linux build/linux/game.x86_64
"$GODOT" --headless --path . --export-release Windows build/windows/game.exe
```

The GitHub Actions build runs these commands and uploads `game-exports`. Serve
`build/web/` over HTTP to try the web game; run the Linux or Windows binary on
its matching platform. No store or signing credentials are needed for these
artifacts. Mobile exports require separate SDKs, platform configuration and
signing. See [Godot export documentation](https://docs.godotengine.org/en/4.5/tutorials/export/index.html).

## Codex cloud environment

Connect GitHub, create a new task and choose **Work in → Cloud → Select
environment → Create environment**, then choose your new repository. Ask Codex
to run `.codex/setup.sh` and the export commands; review setup and output, save
and **Publish**. Start a task: “Change how quickly the player moves, then check
and export the game.” Review its diff and test the result with a teammate.
The coding environment is separate from the GitHub Actions runner. See
[Codex environments](https://learn.chatgpt.com/docs/environments/cloud-environments).

## Optional: deploy the web game

Create a Cloudflare account and a scoped Workers deployment API token. Under
GitHub **Settings → Secrets and variables → Actions**, add repository secrets
`CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID`, and a repository variable
`CLOUDFLARE_WORKER_NAME` with your unique Worker name. Create a GitHub
`production` environment if using protection. Run **Deploy web (manual)**,
then open the Worker URL from the log. No pull request deploys automatically.
The account may have usage limits or costs. Never put real tokens in Git,
prompts or a browser bundle. Other providers use their own credentials and
commands.
