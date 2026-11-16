# zakerimr.github.io

Level design portfolio built with Jekyll and hosted on GitHub Pages.

## Local development

Use Ruby 3.3 — macOS system Ruby (2.6) is too old, and Ruby 4 only resolves an outdated `github-pages`:

```sh
brew install ruby@3.3
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"   # add to ~/.zshrc
bundle install
bundle exec jekyll serve --livereload                # http://localhost:4000
```

If native gems fail with "You have to install development tools first", Xcode is older than the
Command Line Tools SDK. Either run `sudo xcode-select -s /Library/Developer/CommandLineTools`, or add
`export DEVELOPER_DIR=/Library/Developer/CommandLineTools` to `~/.zshrc`.

## Adding a project

1. Create `_projects/<slug>.md` (copy `_projects/example-level.md` — it shows every supported field).
2. Put images in `assets/img/projects/<slug>/` and reference them via `thumbnail`, `hero`, and `gallery`.
3. Set `order` to control position on the home page.

Image fields are optional, so you can add pages before screenshots are ready.

### Front matter fields

| Field | Purpose |
| --- | --- |
| `title`, `summary` | Card and page heading |
| `thumbnail` | 16:9 card image |
| `hero` | Wide banner on the project page |
| `engine`, `role`, `team`, `duration`, `tools` | Sidebar metadata |
| `video` | `{ provider: youtube \| vimeo, id: ... }` embedded at the top |
| `gallery` | List of `{ src, caption }` shown at the bottom |
| `links` | List of `{ label, url }` (e.g. itch.io build) |
| `order` | Sort order on the home page |

Embeds can also be placed inline in the body:

```liquid
{% include video.html provider="youtube" id="VIDEO_ID" %}
{% include gallery.html images=page.gallery %}
```

## Site settings

Edit `_config.yml` for name, description, social links, and resume path (drop a PDF at `assets/resume.pdf` and set `resume: /assets/resume.pdf`).

## Deploying

Push to `main`. In the repo's **Settings → Pages**, set the source to **Deploy from a branch → `main` / root**.
