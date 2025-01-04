# manifest.json

This file is the main manifest file. It contains the following keys:
- `$schema`: string - URL for the associated JSON schema for this file.
- `latest`: object - Contains the latest version of every version type.
- `omnifestVersion`: number - Represents the version of the file. Currently 1.
- `versions`: array - Contains objects corresponding to each version.
  - `id`: string - Used to uniquely identify a version.
  - `type`: string - The type of release a version is. May be one of: `release`, `snapshot`, `april-fools`, or `special`.
  - `url`: string - The url to the [version json file](versions.md).
  - `sha1`: string - The sha-1 hash of the file found at `url`.
  - `time`: string - The last time the version's listing has been updated, formatted as `YYYY-MM-DDTHH:MM:SSZ`.
  - `releaseTime`: string - The time the version was released, or as close an approximation as possible, formatted the same as `time`.
  - `complianceLevel`: number - Indicates whether the version implements player blocking. `1` if true, `0` if false.
  - `mojangVersion`: string - This version's id in mojang's manifest, if applicable; otherwise, null.
  - `equivalentTo`: string - The version id, but without any reupload disambiguation.
  - `phase`: string - The development phase the version was released during. May be one of `pre-classic`, `classic`, `indev`, `infdev`, `alpha`, `beta`, `post-1.0`, or `oddballs`.

## Additions

This file extends upon Mojang's manifest by adding the following keys for each version: `mojangVersion`, `equivalentTo`, `phase`, `type`.

### Version Phases
+ `pre-classic` - private versions from before classic
+ `classic` - versions released originally from 2009-05-16 to 2009-11-10
+ `indev` - versions released from 2009-12-23 to 2010-02-23
+ `infdev` - versions released from 2010-02-27 to 2010-06-30
+ `alpha` - versions released from 2010-07-02 to 2010-12-03
+ `beta` - versions released from 2010-12-20 to 2011-09-15
+ `post-1.0` - full public releases from 2011-09-22 onwards
+ `oddballs` - versions that do not fit in a typical time-based version ordering system

### Version Types
+ `release` - normal release versions
+ `snapshot` - public snapshots, pre-releases, and release candidates
+ `april-fools` - versions published as april fools jokes
+ `special` - any version that doesn't fit into any of the other types

## Removals

The following version types have been removed in favor of the above more accurate organization system: `old_alpha`, `old_beta`.
