# Release

Standalone repo: [AI-Guiders/AIGuiders.DotnetTools](https://github.com/AI-Guiders/AIGuiders.DotnetTools).

## Tag-driven NuGet publish

One workflow (`.github/workflows/publish.yml`), **independent versions per tool** via tag prefix:

| Tag | Package |
|-----|---------|
| `PublishFixedTarget/v0.1.5` | `AIGuiders.DotnetTools.PublishFixedTarget` → CLI `aid-publish` |
| `TomlCheck/v0.1.1` | `AIGuiders.DotnetTools.TomlCheck` → CLI `aig-toml-check` |

```bash
git tag PublishFixedTarget/v0.1.5
git push origin PublishFixedTarget/v0.1.5

git tag TomlCheck/v0.1.1
git push origin TomlCheck/v0.1.1
```

Configure [NuGet Trusted Publishing](https://learn.microsoft.com/en-us/nuget/nuget-quickstart-trusted-publish) on the repo for workflow `publish.yml`.

Manual publish (emergency): **Actions → NuGet publish → Run workflow** — choose package + version.

## Changelog

### TomlCheck

#### 0.1.1

- NuGet metadata: `RepositoryUrl` / `PackageProjectUrl` → [AI-Guiders/AIGuiders.DotnetTools](https://github.com/AI-Guiders/AIGuiders.DotnetTools) (no code changes).

#### 0.1.0

- `aig-toml-check check`: TOML parse (Tomlyn), `#:schema` directive, JSON Schema validation (JsonSchema.Net).

### PublishFixedTarget

#### 0.1.5

- `aid-publish`: `-UseNuGet` → `/p:AidUseNuGet=true` (projects with dual ProjectReference|PackageReference can force NuGet).

#### 0.1.3

- NuGet metadata: `RepositoryUrl` / `PackageProjectUrl` → [AI-Guiders/AIGuiders.DotnetTools](https://github.com/AI-Guiders/AIGuiders.DotnetTools) (no code changes).

#### 0.1.2

- `aid-publish`: optional repeatable `-RequireMirrorFile` — after mirror fails if listed file missing under `Target` (e.g. Roslyn MCP `Microsoft.CodeAnalysis.Workspaces.MSBuild.BuildHost.dll`).

#### 0.1.0

- Add `aid-publish` (`AIGuiders.DotnetTools.PublishFixedTarget`)
  - `dotnet publish` wrapper that mirrors output into a fixed target directory.
  - Optional `-KillRunning` preflight to stop the app if it runs from the target path (avoids file locks).
  - Prints proof timestamps for publish/target.
