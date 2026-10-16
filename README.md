# OpenStudios Lawrence website

This repository is the source for [openstudioslawrence.org](https://openstudioslawrence.org). You can edit it entirely in your web browser. When you commit a change here, the website rebuilds and updates by itself in about a minute.

## Two branches, two websites

| Branch | Website | Who can see it |
|---|---|---|
| `dev` | [dev.openstudioslawrence.org](https://dev.openstudioslawrence.org) | Only people on the list. Log in with your email and you'll be sent a code |
| `master` | [openstudioslawrence.org](https://openstudioslawrence.org) | Everyone |

**Always make your changes on `dev`.** Check them on the dev site, and when they look right, publish them to the live site (see [Publishing to the live site](#publishing-to-the-live-site)). The `master` branch can't be edited directly. If GitHub offers to "create a new branch" or "propose changes" when you save, you're on `master` by mistake. Cancel, switch to `dev`, and make the change there.

## Making a change

1. At the top left of this page, use the branch menu (it usually says `master`) to switch to **`dev`**.
2. Find the file you want:
   - **News posts:** `content/news/`
   - **Storefronts:** `data/storefronts/` (see [STOREFRONTS.md](STOREFRONTS.md) for every field)
   - **Photos:** `static/images/` (see [Photos](#photos))
3. To edit, open the file and click the pencil icon. To add something new, use **Add file** → **Create new file** or **Upload files**.
4. Click **Commit changes** and choose **Commit directly to the `dev` branch**. Add a short note about what you changed.
5. Wait about a minute, then check [dev.openstudioslawrence.org](https://dev.openstudioslawrence.org).

## Did it work?

Next to your commit (and on the **Actions** tab), GitHub shows a status:

- 🟡 **Yellow dot:** still building. Give it a minute.
- ✅ **Green check:** published.
- ❌ **Red X:** something in your change stopped the site from building. **Nothing was published, and the website is unchanged.** Open the **Actions** tab and click the failed run. Under **Annotations**, the error names the **file and line** with the problem, and the file name links straight to that line. Fix it and commit again.

## Adding a news post

Create a new file in `content/news/`. Name it with no spaces, ending in `.md` (for example `octoberNewsletter.md`). Start it like this:

```
---
title: "October Newsletter: three new artists!"
date: 2026-10-15
description: "A short summary that appears on the News page."
---

The full text of the post goes here. You can use *italics*, **bold**, and
[links](https://example.com).
```

- The newest `date` becomes the "Latest News" on the home page.
- **A date in the future hides the post** until that day, and the site has to be rebuilt after that day for it to appear. Commit any small change on or after that day, or ask John.
- The description can include simple HTML like `<i>The Livingroom Collective</i>`. **Always close tags.** A missing `</i>` will scramble the News page.

## Storefronts

Each storefront is one file in `data/storefronts/`. Storefronts appear on the home page in filename order, which is why the files start with `01-`, `02-`, and so on.

- To **change** a storefront, edit its file. [STOREFRONTS.md](STOREFRONTS.md) explains every field and has a complete example.
- To **add** one, create a new file in `data/storefronts/` (for example `04-123-mass-st.yaml`), paste in the contents of an existing storefront file or the example in [STOREFRONTS.md](STOREFRONTS.md), and change the details.
- To **remove** one, delete its file.

These files are YAML, which is picky about spacing:

- Indent with **spaces, never tabs**, and keep lines at the same level lined up exactly.
- If a value contains a double quote, write it as `\"`. Example: `bio: "She calls it \"junk art.\""`

When the build fails because of a storefront file, the error will usually say "did not find expected key" or similar, with a line number. Check the spacing on that line and the one above it.

## Photos

Every file under `static/` is published at the same path **without** the `static` part. So a photo uploaded to `static/images/example.jpg` is referred to as `/images/example.jpg`.

Where to put them:

- **Storefront photos** go in that storefront's folder, `static/images/storefronts/<storefront folder>/`. In the storefront file:

  ```
  image: "/images/storefronts/percolator/jane.jpg"
  ```

- **Photos for news posts and pages** go directly in `static/images/`. To show one in a news post:

  ```
  ![Description of the photo for people who can't see it](/images/october-opening.jpg)
  ```

Please resize photos before uploading. Around 1,500 pixels wide and under 1 MB is plenty, and the site loads faster. Avoid spaces in file names.

How storefront photos are shown:

- **Artist photos** appear as squares on computers and as a wide strip on phones, cropped from the top. If a face gets cut off on phones, add `imagePosition` to that artist (see [STOREFRONTS.md](STOREFRONTS.md)).
- **The storefront photo** fills the page width and is cut to at most 400 pixels tall. Wide, landscape shots at least 1,200 pixels wide work best. Tall photos and posters lose most of their content. To show a different photo on phones, use `photoMobile`.
- **Sideways or upside-down photos:** phones often save a photo in one orientation with a note saying "rotate this." Some editing and resizing tools drop that note, and the photo then comes out sideways. If that happens, rotate the photo in an editor and save it again before uploading.

## Sending a preview to someone for approval

Artists and others outside the team can't log in to the dev site, but every change on `dev` also gets its own **shareable preview link** that needs no login.

1. After you commit to `dev`, open the **Actions** tab and click your run.
2. Once it has finished (green check), the **Annotations** box shows **Shareable preview of this version** with a link like `https://1a2b3c4d.openstudioslawrence.pages.dev`.
3. Copy that link into your email to the artist.

The link always shows exactly that version, even if you make more changes on `dev` afterward. It isn't password-protected, but it's random and search engines are told to ignore it, so only people you send it to will see it. If you make changes after their feedback, send them the new link from the newer run.

## Publishing to the live site

When the dev site looks right:

1. Go to **Pull requests** → **New pull request**.
2. Set **base** to `master` and **compare** to `dev`. GitHub shows every change that will go live. Look it over.
3. Click **Create pull request**, then **Merge pull request**, then **Confirm merge**. The merge button stays disabled until the dev site's build has succeeded, so a broken change can't reach the live site.
4. About a minute later, the live site is updated.

## Undoing a mistake

- **On the dev site:** just edit the file again and commit, or ask for help.
- **On the live site:** tell John. Cloudflare keeps every past version of the site, and any of them can be restored in seconds.

---

## For maintainers

- **Built with** [Hugo](https://gohugo.io/) 0.154.5 (extended) and the [hugo-profile](https://github.com/gurusabarish/hugo-profile) theme, which is included as a git submodule (`git clone --recurse-submodules`). Site-specific layouts in `layouts/` override the theme.
- **Local preview:** `hugo server` reloads the browser as you save. Use it for layout and CSS work instead of waiting on deploys.
- **Deploys:** `.github/workflows/deploy.yml`. Pushes to `master` and `dev` are built by GitHub Actions and uploaded to the Cloudflare Pages project `openstudioslawrence`. A failed build deploys nothing. The workflow needs the `CLOUDFLARE_API_TOKEN` repository secret, a token limited to Cloudflare Pages: Edit. To change the Hugo version, edit `HUGO_VERSION` in the workflow.
- **Anything the site serves must be in the repo.** Files that aren't generated by Hugo go in `static/`. Nothing is hand-placed on a server anymore.
- **Never commit passwords or tokens.** This repository is public.
