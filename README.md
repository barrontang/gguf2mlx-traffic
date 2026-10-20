# gguf2mlx-traffic

Repository traffic tracking for [gguf2mlx](https://github.com/barrontang/gguf2mlx),
split out of the main repository on 2026-10-20.

It lives here because the tracker is **GPL-3.0-or-later** while `gguf2mlx` is
Apache-2.0, and because it needs a long-lived `TRAFFIC_GIST_TOKEN` secret that
has no business sitting in a package repository.

## What is in here

| Path | Purpose |
|---|---|
| `.github/workflows/traffic-badges.yml` | Daily clone/view collection, writes JSON to a Gist and rebuilds the dashboard |
| `docs/stats/index.html` | Static dashboard published via GitHub Pages |
| `docs/stats/favicon.svg` | Dashboard icon |
| `docs/images/ghtraf-*.png` | Badge/banner art |
| `LICENSES/GPL-3.0.txt`, `LICENSES/GPL-3.0-NOTICE.md` | Upstream license and scope notice |

## Setup

```bash
pip install github-traffic-tracker
ghtraf create --owner barrontang --repo gguf2mlx --configure \
  --repo-dir /absolute/path/to/gguf2mlx-traffic
gh secret set TRAFFIC_GIST_TOKEN
```

Then enable GitHub Pages for this repository from the `main` branch, `/docs`
directory. The workflow stays skipped until `TRAFFIC_GIST_ID` is configured.

## License

The tracking workflow and dashboard are GPL-3.0-or-later; see
`LICENSES/GPL-3.0.txt`. Everything here is unrelated to the `gguf2mlx` package
license, which remains Apache-2.0.
