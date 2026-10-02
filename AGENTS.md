# How to work in this repository

This is the GitHub profile repository: `README.md` here is what renders on
`https://github.com/rtf6x`.

## Cards

`assets/<card>.<theme>.svg` are **generated** by
[`seijikohara/profile-cards-action`](https://github.com/seijikohara/profile-cards-action)
from `.github/workflows/profile-cards.yml` — daily at 00:00 UTC and on manual
dispatch. Do not edit them by hand; the next run overwrites the file.

Change the card set, the themes or the badge pills in the workflow inputs, then
run it again:

```bash
gh workflow run profile-cards.yml --repo rtf6x/rtf6x
gh run watch --repo rtf6x/rtf6x
```

The workflow commits its own output back to `master`.

## Token

The action authenticates with the `PROFILE_TOKEN` repository secret: a classic
PAT with the `repo` and `read:user` scopes. `GITHUB_TOKEN` is not enough — it is
scoped to this repository, so private repositories stay invisible to the
cadence sweep and private contributions are undercounted.

Replace it at <https://github.com/rtf6x/rtf6x/settings/secrets/actions>.

## README

Each card is embedded as a `<picture>` with the light and dark SVG, so the card
matches the viewer's GitHub theme. Keep that shape when adding a card.
