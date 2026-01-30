# nickphillips.dev

Personal blog and portfolio site built with [Hugo](https://gohugo.io) and the [Blowfish](https://blowfish.page) theme.

## Prerequisites

- [Hugo](https://gohugo.io/installation/) (extended version recommended)
- Git (for submodule support)

## Local Development

```bash
# Clone with submodules
git clone --recurse-submodules https://github.com/phillipsnick/nickphillips.dev.git
cd nickphillips.dev

# If you already cloned without submodules
git submodule update --init --recursive

# Start dev server with live reload
hugo server
```

The site will be available at `http://localhost:1313`.

## Creating Content

```bash
# New post (created as draft by default)
hugo new content/posts/my-post-title.md
```

Set `draft = false` in the front matter when ready to publish.

## Deployment

Pushing to `main` automatically triggers a GitHub Actions workflow that:

1. Builds the site with `hugo --minify`
2. Publishes the output to the `gh-pages` branch
3. GitHub Pages serves the `gh-pages` branch at [nickphillips.dev](https://nickphillips.dev)

No manual deployment steps are needed.

## Configuration

All configuration lives in `config/_default/`. Key files:

| File | Purpose |
|------|---------|
| `hugo.toml` | Core Hugo settings |
| `params.toml` | Theme appearance and layout options |
| `languages.en.toml` | Author profile and social links |
| `menus.en.toml` | Navigation menu entries |

Full theme documentation: [blowfish.page/docs](https://blowfish.page/docs/)

## Contributing

Spotted a typo or broken link? PRs are welcome.

1. Fork the repo
2. Create a branch (`git checkout -b fix/typo-in-post-title`)
3. Commit your changes
4. Open a pull request against `main`

## License

Hugo configuration and assets are released under the [Apache 2.0 license](LICENSE).

All content and images are Copyright Nick Phillips. All rights reserved.
