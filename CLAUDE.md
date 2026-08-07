# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project state

This is a brand-new Godot project named **BankSim**, currently just past initial scaffolding. There is no gameplay code yet:

- `scenes/`, `scripts/`, `ui/`, `assets/` exist but are empty.
- `node_2d.tscn` is a placeholder scene (a single empty `Node2D`).
- No `.csproj`/`.sln` exists yet, even though the project is configured for .NET (see below).

Treat any architectural description here as provisional — update this file as real structure is introduced, since there isn't much to derive from the code yet.

## Engine configuration (`project.godot`)

- **Godot version**: 4.7, GL Compatibility rendering feature profile.
- **Renderer**: `gl_compatibility` on both desktop and mobile (not Forward+/Mobile).
- **Rendering device (Windows)**: `d3d12`.
- **.NET/C#**: enabled — `[dotnet] project/assembly_name="BankSim"`. When C# scripts are added, a `.sln`/`.csproj` will need to be generated (Godot does this automatically the first time a C# script is created in the editor, or via `dotnet new`).
- **Physics**: 3D physics engine is Jolt Physics (not the Godot default).
- **Display stretch**: `canvas_items` mode with `expand` aspect — this is a 2D-scaled project setup even though 3D physics (Jolt) is configured, so don't assume the project is purely 2D or purely 3D from this alone.

## Editing `project.godot`

This file is hand-editable but the header explicitly warns it's best edited via the Godot editor UI, since not all parameters are obvious/documented. Prefer making engine-setting changes through the editor when possible; when editing directly, keep the section/key format consistent with the existing file. A `project.godot.bak` backup exists from a prior editor save — don't treat it as a file to edit or keep in sync.

## Version control notes

- `.gitattributes` normalizes all text files to LF line endings.
- `.godot/` (Godot's local cache/import directory) is gitignored — never treat files under it as source.
- `.summer/local/` is gitignored — it holds local-only state for a "Summer Engine" tooling layer wrapping this repo (including its own nested bare git repo under `.summer/local/git/`). This is tooling-local, not project source; don't edit or commit through it.

## Development workflow

There is no build/lint/test tooling set up yet (no C# project file, no test framework, no CI config). Since there's no `.csproj`, C# scripts can't be compiled outside the Godot editor until one is generated. Running/testing changes currently means opening the project in the Godot 4.7 editor and using its Play/Run functionality; update this section once scripts, scenes, and a test setup exist.
