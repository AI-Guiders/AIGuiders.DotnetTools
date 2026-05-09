# Release

This folder is meant to be copy-pasted into the standalone repo (`AIGuiders.DotnetTools`).

## 0.1.2

- `aid-publish`: optional repeatable `-RequireMirrorFile` — after mirror fails if listed file missing under `Target` (e.g. Roslyn MCP `Microsoft.CodeAnalysis.Workspaces.MSBuild.BuildHost.dll`).

## 0.1.1

- Fix GitHub Actions `publish.yml` pack/push paths for the standalone repo layout.

## 0.1.0

- Add `aid-publish` (`AIGuiders.DotnetTools.PublishFixedTarget`)
  - `dotnet publish` wrapper that mirrors output into a fixed target directory.
  - Optional `-KillRunning` preflight to stop the app if it runs from the target path (avoids file locks).
  - Prints proof timestamps for publish/target.
