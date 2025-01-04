# version.json

This file is a JSON object representing a Minecraft version. It contains the following keys:
- `$schema`: string - URL for the associated JSON schema for this file.
- `arguments`: object - Contains two arrays of strings, `game` and `jvm`, which are arguments to be passed to Minecraft itself and the Java Virtual Machine, respectively.
- `id`: string - Used to uniquely identify a version.
- `downloads`: object - See [here](#download).
- `libraries`: object - See [here](#libraries).
- `time`, `releaseTime`, `type`, `phase`, `complianceLevel`: [See manifest.md for possible values and descriptions.](manifest.md)
- `mainClass`: string - The main class path in the version jar file. May be null.
- `javaVersion`: object - Contains the keys `majorVersion`, `component`, and `minVersion`.
    - `majorVersion`: number - The recommended major java version to run the game with.
    - `component`: string - Which of Mojang's [java runtimes](https://launchermeta.mojang.com/v1/products/java-runtime/2ec0cc96c44e5a76b9c8b7c39df7210883d12871/all.json) to launch the game with.
    - `minVersion`: number - The minimum java version supported by this version of the game. Must be less than or equal to `majorVersion`.
- `assetIndex`: object - See [here](#index).
- `assets`: string - The id of the assetIndex to use.
- `clientJsonVersion`: number - Represents the version of the file. Currently 1.

## Objects
### Download
This contains download information for different components of the version.
- `[type]`: object - Download information for a specific component. Possible types are `client`, `client_mappings`, `server`, `server_mappings`, and `windows_server`.
  - `url`: string - The url to the component file.
  - `sha1`: string - The sha-1 sum of the file at `url`.
  - `size`: number - The size of the file in bytes.

### Libraries
This contains a list of libraries to be downloaded and used by the game.
- `name`: string - The name of the library.
- `rules`: optional object - A list of rules to determine whether this library should be loaded. See [library rules](#library-rules).
- `extract`: optional object - A list of files to be excluded when extracted.
  - `exclude`: string array - will only ever contain "META-INF/"
- `downloads`: object - Download information for this library.
  - `classifiers`: optional object - Contains objects for this library's classifiers, each formatted like `artifact`. Possible names are `javadocs`, `sources`, `linux-x86_64`, `natives-linux`, `natives-macos`, `natives-osx`, `natives-windows`, `natives-windows-32`, `natives-windows-64`.
  - `artifact`: object - Download information for this library's main artifact.
    - `path`: string - The local path this artifact should be stored at.
    - `sha1`: string - The sha-1 sum of the file at `url`.
    - `size`: number - The size of the file in bytes.
    - `url`: string - The url to the artifact file.
- `natives`: optional object - A map of operating systems to classifier names. Each key is one of `windows`, `osx`, or `linux`, and each value is a classifier key.

### Library Rules
This contains a list of rule objects to determine whether a library should be loaded. If there are multiple rules, these will be evaluated in order.
- `action`: string - The action to take if this rule is matched. May be one of `allow` or `disallow`.
- `os`: optional object - The operating system this rule applies to.
  - `name`: string - The name of the operating system. Can be one of `windows`, `osx`, or `linux`.
  - `version`: optional string - The version of the operating system. Matches using regex. Only used for `osx`.

### Index
This contains download information for this version's asset index. For more information about these files, see [the asset index documentation](indexes.md).
- `id`: string - The identifier for this asset index.
- `sha1`: string - The sha-1 sum of the file at `url`.
- `size`: number - The size of the index's .json file.
- `totalSize`: number - The sum of the sizes of all assets in the index
- `url`: string - The url to the asset index's .json file.
