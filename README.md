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

## Image Metadata

Photos straight off a phone or camera carry EXIF metadata: GPS coordinates,
camera serial number, owner name, and capture timestamps. Hugo copies page
bundle originals into the built site **byte for byte** — the full resolution
file is published exactly as it sits in the repo, alongside the resized
variants. Nothing in the build strips metadata for you, so it has to be removed
at source before committing.

Strip it with [ExifTool](https://exiftool.org) (`brew install exiftool`):

```bash
# Check what an image is carrying
exiftool -a -G1 -s path/to/image.jpg

# Strip a single image
exiftool -all= -tagsfromfile @ -Orientation -ICC_Profile -overwrite_original path/to/image.jpg

# Strip everything under content/ recursively
exiftool -all= -tagsfromfile @ -Orientation -ICC_Profile -overwrite_original \
  -r -ext jpg -ext jpeg -ext png content/
```

The `-tagsfromfile @ -Orientation -ICC_Profile` part matters. A bare
`exiftool -all=` also removes the orientation flag and the colour profile, which
makes phone photos display rotated and can visibly shift colours. Those two tags
carry nothing sensitive, so they are worth keeping.

`-overwrite_original` edits in place. Drop it if you would rather ExifTool left
`.jpg_original` backups behind.

To confirm a directory is clean — this prints nothing when there is nothing
left to find:

```bash
exiftool -r -if '$GPSLatitude or $SerialNumber or $OwnerName' \
  -filename -GPSPosition -SerialNumber -OwnerName content/
```

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
