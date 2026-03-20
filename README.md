# HârnWorld Campaign: The Earl's Progress
[![Version (latest)](https://img.shields.io/github/v/release/toastygm/hm-cpn-earlsprogress)](https://github.com/toastygm/hm-cpn-earlsprogress/releases/latest)
[![Forge Installs](https://img.shields.io/badge/dynamic/json?label=Forge%20Installs&query=package.installs&suffix=%25&url=https%3A%2F%2Fforge-vtt.com%2Fapi%2Fbazaar%2Fpackage%2Fhm-cpn-earlsprogress&colorB=4aa94a)](https://forge-vtt.com/bazaar#package=hm-cpn-earlsprogress)
[![GitHub downloads (latest)](https://img.shields.io/badge/dynamic/json?label=Downloads@latest&query=assets[?(@.name.includes('zip'))].download_count&url=https://api.github.com/repos/toastygm/hm-cpn-earlsprogress/releases/latest&color=green)](https://github.com/toastygm/hm-cpn-earlsprogress/releases/latest)

This module provides the campaign "The Earl's Progress", a campaign for the
[HârnWorld](https://columbiagames.com/harnworld/) fantasy setting. However, this
campaign could be located in any fantasy setting or location with some adaptations.

Although designed for use with the [HârnMaster](https://foundryvtt.com/packages/hm3)
system, this module is mostly system-agnostic, with the exception of Actors.
Detailed descriptions of the actors has been provided in journal entries to facilitate
conversion to other game systems.

_The Wyvern Stirs..._

**Sir Declaen Caldeth**, 19th Earl of Vemion, prefers his remote fiefdom and the security of Minarsas Castle to the politics and intrigue of the Royal Court of Kaldor. He rarely stirs from his lair, and then only for the briefest of periods. Thus, his subjects were shocked when he announced his intention to make a great tour of the realm. He will visit his liegeman, the Baron of Kolorn and his Constables at Zoben and Baseta, attend the Royal Chelebin Tournament of Chivalry at Olokand Castle and stop at the capital city of Tashal en route.

All of Vemionshire is abuzz with the news. The Earl will host a tournament in Minarsas. The winners will join his retinue and represent the shire at the Olokand tourney. Every knight and yeoman is vying for a spot in this once-in-a-lifetime tour of the kingdom and with it, the promise of the personal favor of one of the most powerful magnates in Kaldor. Are you worthy of being a member of The Earl’s Progress?

# Credits

This module is made possible by the hard work of HârnWorld fans, and is provided at no
cost. This work is an adaptation of the adventure
[The Earl's Progress](https://www.lythia.com/adventures/earls-progress/) available at
the HârnWorld fan site [Lythia.com](https://www.lythia.com/).

**Writer:** Kerry Mould

**Illustrations:** Richard Luschek

**Adapted to Foundry VTT:** Tom Rodriguez

This module is "[Fanon](https://www.lythia.com/about/publishing-fan-written-material/)", a derivative work of copyrighted material by Columbia Games Inc. and N. Robin Crossby.



# Development

Requires Node.js >= 24.

## Project structure

- `assets/packs/<name>/unique/` — source JSON files for each compendium pack
- `assets/templates/module.template.json` — module manifest template (version/URLs are injected at build time from `package.json`)
- `scripts/init.js` — ScenePacker integration
- `utils/` — build scripts

## Common tasks

```sh
npm install                  # install dependencies (first time / after pulling)
npm run deploy:qa            # build and deploy to local QA Foundry instance
npm run deploy:release       # build and create build/dist/module.zip
npm run release              # create GitHub release (needs GITHUB_TOKEN)
npm run clean                # remove build/
```

## Making content changes

Edit the JSON files in `assets/packs/<name>/unique/`. These are the source of truth — LevelDB packs are compiled from them at build time.

## Deploying locally for testing

Set environment variables for your Foundry data paths (in `.env.local` or your shell):

```
FOUNDRYVTT_DEV_DATA=/path/to/foundry/dev
FOUNDRYVTT_QA_DATA=/path/to/foundry/qa
FOUNDRYVTT_PROD_DATA=/path/to/foundry/prod
```

Then `npm run deploy:qa` (or `:dev` / `:prod`) will build and rsync to that instance.

## Releasing

1. Bump the version in `package.json`
2. Commit and push to `main`
3. `npm run deploy:release` — builds and creates `build/dist/module.zip`
4. `export GITHUB_TOKEN=$(gh auth token)` (or set in `.env.local`)
5. `npm run release` — creates a GitHub release with `module.zip` and `module.json` attached
