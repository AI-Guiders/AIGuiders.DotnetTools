# AIGuiders.DotnetTools

Small, pragmatic .NET tools used across AIGuiders projects.

## Tools

- **`aid-publish`** (`AIGuiders.DotnetTools.PublishFixedTarget`): wrapper around `dotnet publish` that
  - mirrors output into a fixed target path,
  - optionally kills the app only if it runs from that target path (file-lock preflight),
  - prints proof timestamps,
  - optionally `-RequireMirrorFile` to assert critical files after mirror (e.g. Roslyn MSBuild Workspace `BuildHost-netcore`).

## Install as a local tool (recommended)

In a repo root:

```bash
dotnet new tool-manifest
dotnet tool install AIGuiders.DotnetTools.PublishFixedTarget
dotnet tool restore
```

Run:

```bash
dotnet aid-publish -Help
```

