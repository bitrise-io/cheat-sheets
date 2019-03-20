# Swift CLI

- `swift package init --type executable` : Init a swift (swift package manager based) project.
- `swift package update` : After changing `Package.swift` call this to apply the changes.
- `swift package generate-xcodeproj` : Generate an Xcode project for the Swift Package Manager based project.
- `swift build` : Building the SPM project. Generates executable under `.build/debug/`
- `swift run PackageName` : This is basically the same as `swift build` and then running the `.build/debug/PackageName` binary.
    - e.g. `swift run CommandLineTool --help` or `swift run CommandLintTool --number 4` to pass some args to it.
