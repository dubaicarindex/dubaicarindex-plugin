# Contributing

Thanks for taking the time.

## Before you open a PR

**Most of this repo is generated** from the Dubai Car Index source and is
overwritten on every sync: the manifests, `.mcp.json`, `mcp.json`, `skills/`,
`assets/`, `README.md` and `LICENSE`. A PR against those will be lost.

If one of them is wrong, open an issue saying which file and what is wrong with
it, and it gets fixed at the source.

## What is most useful

- **A skill that leads the assistant astray.** A list price quoted without its
  source or date, a modelled used value or rental rate presented as a market
  price, a question it should have refused. Include the prompt.
- **A tool that disagrees with the site.** If a figure differs from the same
  brand, model, year, rental or repair page on dubaicarindex.com, say which
  page and which figure.
- **Install trouble.** Which client, which version, and the error.

Do not include sign-in links, codes or tokens.

## Security

Do not open an issue. See [SECURITY.md](./SECURITY.md).
