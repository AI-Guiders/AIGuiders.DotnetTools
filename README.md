# AIGuiders.DotnetTools

Small, pragmatic .NET tools used across AIGuiders projects.

## Tools

| CLI | NuGet package | Purpose |
|-----|---------------|---------|
| `aid-publish` | `AIGuiders.DotnetTools.PublishFixedTarget` | `dotnet publish` → fixed target mirror, optional kill-locking process, proof timestamps |
| `aig-toml-check` | `AIGuiders.DotnetTools.TomlCheck` | TOML + JSON Schema (`#:schema` directive) |

### aid-publish

- mirrors output into a fixed target path,
- optionally kills the app only if it runs from that target path (file-lock preflight),
- `-UseNuGet` → `/p:AidUseNuGet=true` (prefer PackageReference when project supports it),
- prints proof timestamps,
- optionally `-RequireMirrorFile` to assert critical files after mirror (e.g. Roslyn MSBuild Workspace `BuildHost-netcore`).

### aig-toml-check

- reads `#:schema path.json` from TOML headers (Taplo-style),
- parses with Tomlyn, validates with JsonSchema.Net,
- `check <files-or-dirs>` exit code 0/1.

## Install as local tools

In a repo root:

```bash
dotnet new tool-manifest
dotnet tool install AIGuiders.DotnetTools.PublishFixedTarget
dotnet tool install AIGuiders.DotnetTools.TomlCheck
dotnet tool restore
```

```bash
dotnet aid-publish -Help
dotnet aig-toml-check check IntentMelody/intent-catalog.toml
```

## Release

Tag prefix per tool — see [docs/release.md](docs/release.md).

