# Changelog Entry Format

Based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## File Structure

```markdown
# Changelog

All notable changes to this project are documented here.

## [Unreleased]

## [1.2.0] - 2026-03-18
### Added
- New feature X that does Y

### Changed
- Updated Z to behave differently

### Fixed
- Resolved issue where A caused B

[Unreleased]: https://github.com/owner/repo/compare/v1.2.0...HEAD
[1.2.0]: https://github.com/owner/repo/compare/v1.1.0...v1.2.0
```

## Categories (use only what applies)

| Category    | When to use |
|-------------|-------------|
| `Added`     | New features, endpoints, commands, config options |
| `Changed`   | Changes to existing behavior, API, or output |
| `Deprecated`| Features that will be removed in a future version |
| `Removed`   | Features, files, or options that were deleted |
| `Fixed`     | Bug fixes, error handling, incorrect behavior |
| `Security`  | Patches for vulnerabilities or security improvements |

## Versioning Strategy

- **Unreleased work** → append under `## [Unreleased]`
- **Creating a release entry** → replace `[Unreleased]` with `[X.Y.Z] - YYYY-MM-DD`
- Follow [SemVer](https://semver.org/): MAJOR.MINOR.PATCH

## Writing Good Bullets

**Pattern:** `- <Verb> <what> [so that / to / for] <why/benefit>`

Good examples:
```
- Add speaker diarization to transcription pipeline for multi-speaker recordings
- Fix race condition in session store when concurrent writes occur
- Remove deprecated /v1/audio endpoint (use /v2/audio instead)
- Change default model from whisper-small to whisper-large-v3 for accuracy
```

Bad examples:
```
- Updated some files                    # too vague
- Fixed the bug                         # which bug?
- Added transcription.ts and model.ts   # lists files, not behavior
```

## Placement in CHANGELOG.md

When appending new work:

1. If `## [Unreleased]` section exists → insert bullets under it
2. If no `## [Unreleased]` section → insert a new `## [Unreleased]` block at the top (after `# Changelog` header)
3. If CHANGELOG.md does not exist → create it with the full header and the new entry
