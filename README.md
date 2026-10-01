# Actions

Useful combination of reusable workflows found on Lunaris projects.

## Build

Builds your CMake project, setting up MSVC, MinGW or GCC (so far).

Parameters:
- `compiler`: One of the options: `gcc` (Linux), `msvc` (Windows), or `mingw` (Windows).
- `shell`: The shell used by the application. Defaults to `bash` (cross-platform), but with MinGW you may consider `msys2 {0}` instead.
- `install`: Whether to run CMake install and upload the generated install folder.
- `upload_executable`: Whether to upload the final executable or not.
- `test`: Wether to run CTest or not.

**IMPORTANT NOTE** for `upload_executable`: You MUST add `install(TARGETS ${PROJECT_NAME} DESTINATION bin)` to your project for it to work properly. This enables it to copy the executable equally on all platforms.

## InstallAllegro5

Installs Allegro 5 in the system.

Parameters:
- `os`: Which OS, `windows-latest` or `ubuntu-latest` (for now).

## Release

Gets all generated files and put on a release as files. Useful to run targeting a branch created on release creation.

## Versioning

Useful tool to commit in an orphan branch and keep track of versioning in a pipeline.

Parameters:
- `kind`: What kind of release: `M` for Major, `m` for minor, `r` for revision / patch, `rc` for release candidate, `snapshot` for snapshot.
- `path`: The path used for the files of this action in its branch. Defaults to `_versioning`.
- `project`: The project name, if you want to have multiple version handling in the same repository. Optional.
