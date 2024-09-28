## Intro

This is the repo for the WhaleplaneStudios website. It's just a small site to show off our games and display a bit of info about the company.

To any future WhaleplaneStudios members working on this: if you are used to web development this'll be very straightforward to edit. If not, here's a quick rundown of how it works:
- Node-based web dev is terrible on Windows, so use WSL or a Linux VM
- I recommend VS Code as an editor, especially because you get "format on save" to align tabs, spaces, brackets, etc automatically
- "Sveltekit" is the whole Node framework for the site, which uses "Svelte" for frontend HTML
- Typescript is based on Javascript, so if you can't find a Typescript answer/solution to something a Javascript one should work too
- Tailwind is how we're doing styling (instead of regular CSS), that's the `class=` tags you see
- `routes/+page.svelte` is the "main page" that you'll probably be editing the most. Custom stuff for that page is broken out into components in the `lib/components` folder, and the stuff in the `lib/components/ui` is from shadcn-svelte


## Tools

- Github Pages (Hosting)
- Sveltekit (Framework)
- Tailwind (CSS)
- shadcn-svelte (Components)


## Development

```bash
pnpm run dev

# or start the server and open the app in a new browser tab
pnpm run dev --open
```


## Building

Before merging to main on Github Pages, you should build and preview the site.

To build the production version:

```bash
pnpm run build
```

Then to preview the production build:

```bash
pnpm run preview
```