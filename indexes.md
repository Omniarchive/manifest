# index.json

These files are JSON objects containing all assets needed to be downloaded for a certain version for the game to play properly. It contains only one key, `objects`, which is an object containing keys corresponding to each asset.
Each asset key is itself an object, named after the asset's file path, containing the following values:
- `hash`: string - The sha-1 sum of the asset file.
- `size`: number - The size of the asset file in bytes.
- `url`: optional string - The URL of the file.

## Additions

These files extend upon Mojang's asset index format by adding the optional `url` key. 
All asset files are normally downloaded from `resources.download.minecraft.net` at a path derived from the `hash`,
however, not all assets are available at that domain, so the `url` key provides a custom url for missing assets to be downloaded from.
