# Voxgig assessment notes

## Task 1: Build an SDK and write a report

- **Build** an open-source SDK under the MIT License in my own GitHub/GitLab account, and **write a short report** on my observations. I keep the copyright and may reference the work elsewhere.
- **Use the Voxgig SDK generator** — AI-assisted or manual is fine.
- **Pick an API** not already in the [catalogue](https://github.com/orgs/voxgig-sdk/repositories). Prefer a SaaS free trial, or a personal project with an API (an API key is needed to test fully).
- **Time-box my human work to 30 minutes.** Going over is fine. Note issues and bugs in the report.
- The report should cover my **developer experience with the generator**, which is what they are most interested in.

## Human journey

This is my personal journey to learn how to generate an SDK, starting from the website as a human would.

### SDK main page

Go to https://voxgig.com/sdk

![Voxgig SDK landing page](image.png)

> [!NOTE]
> Nothing interesting.

#### ⚠️ SPOILER ⚠️

When I scroll down to https://voxgig.com/sdk#your-own-sdk

![The "Your own SDK" section with the npm create command](image-2.png)

That link goes to: https://github.com/voxgig/sdkgen

In the [voxgig-sdkgen section of the README](https://github.com/voxgig/sdkgen#voxgigsdkgen), I finally find what I was looking for:

![README section showing the quick-start commands](image-7.png)

> [!NOTE]
> That repo's `README.md` and the [agent guide](https://voxgig.com/sdk/agents.md) are ❤️fantastic❤️.
>
> That content is what I would like to see on the home page.
>
> As a user, I expect the website to have a complete, up-to-date "Getting started" section, so I do not have to go to the GitHub repo.

**⚠️ But this is a shortcut: as a user, I want to find everything I need on the website, not in the GitHub repo. ⚠️**

### SDK > docs

URL: https://www.voxgig.com/sdk/docs

Docs page. This is where I really expect to find structured technical documentation. But I cannot find it.

#### `Toolchain documentation` section

![The "Toolchain documentation" heading](image-3.png)

> [!NOTE]
> I don't like `Toolchain documentation` as a title. I want to generate an SDK from an API; what does this have to do with a toolchain?

#### `The Pipeline` section

URL: https://voxgig.com/sdk/docs#the-components

![The pipeline table](image-4.png)

> [!NOTE]
> At first glance this looks like a real "Getting started". But after reading it, I realize it is marketing copy rather than a technical guide.
> - We are on the docs page; why not have the getting started here, similar to what is in [`AGENTS.md`](https://github.com/voxgig/create-sdkgen/blob/main/AGENTS.md)?
> - I see mentions of several Voxgig products, like `apidef` and `sdkgen` (the reason I am here), but no mention of `create-sdkgen`, the product I am actually going to use ➡️ It feels confusing; why not link to those products?

#### `The Components` section

I scroll down to [The components](https://voxgig.com/sdk/docs#the-components)


![The components section](image-5.png)

> [!NOTE]
> - A description of the tools, but it does not say which one to use to generate my SDK.
> - Still looking for real documentation and a getting-started guide.
> - This is the first time I see `create-sdkgen`; what is the difference between it and `sdkgen`?
> - 💀 At this point I am lost and frustrated; I don't know what to do.

#### `Where to start` section

I scroll to the bottom of the page, [Where to start](https://voxgig.com/sdk/docs#where-to-start) section

![The "Where to start" section](image-6.png)

> [!IMPORTANT]
> 🎉🎉🎉 FINALLY!!!! `Building an SDK for your own API: start at create-sdkgen` 👈 This is what I have been looking for since the beginning!

**⚠️ At this point I give up on the website and go straight to the `create-sdkgen` GitHub repo, since now I know this is what I need. ⚠️**

### Following `create-sdkgen` README.md

Let's to the [Quickstart](https://github.com/voxgig/create-sdkgen/tree/main#quickstart)

```sh
# 1. Scaffold a project from your OpenAPI 3 spec
create-sdkgen my-api -d ./openapi.yaml -o ./my-api-sdk

# 2. Add the languages you want + offline test mode
cd my-api-sdk/.sdk
npx voxgig-sdkgen target add ts py go
npx voxgig-sdkgen feature add test

# 3. Generate the SDKs (builds the .sdk sources, then runs the generator)
npm run generate

# 4. Verify
cd ../ts && npm install && npm run build && npm test
```

## Robot journey

If I ask an AI what the steps to complete the assessment are, it is very clear what I have to do.

### Prerequisites

- Node.js 24+ (`node -v`)
- Git and a GitHub account
- Your `openapi.json` file

### Step 1 — Scaffold the project

Open a terminal in the folder holding your `openapi.json`:

```sh
npm create @voxgig/sdkgen@latest -- my-api -d ./openapi.json -o ./my-api-sdk -t ts -f test
```

This creates `my-api-sdk/`. Inside it, `.sdk/` is your project; `ts/` will hold the generated SDK. `-t ts` = generate TypeScript; `-f test` = include the offline test suite.

### Step 2 — Generate the SDK code

```sh
cd my-api-sdk/.sdk
npm run generate
```

This reads `.sdk/model/` and writes the SDK into `ts/`.

### Step 3 — Build and test it

```sh
cd ../ts
npm install
npm run build
npm test
```

Green tests = the SDK works, offline, no API key needed.

### Step 4 — (Optional) One real call

Only if you have an API key: make a single live request to prove it works end to end. If you don't have a key, skip this — the offline tests still prove the SDK builds and runs against the mock.

### Step 5 — Push to your GitHub under MIT

```sh
cd ..                       # back to my-api-sdk/
git init && git add . && git commit -m "Initial SDK"
# create an empty repo on GitHub, then:
git remote add origin https://github.com/pablorotten/my-api-sdk.git
git push -u origin main
```

Add a `LICENSE` file with the MIT text (or let the scaffold's license stand).

### Step 6 — Write the report

Repo URL + what worked, what broke, where you got stuck, what you'd change. That's what Richard actually wants.

If something looks wrong in the output (wrong entity names, missing operations): edit the files in `my-api-sdk/.sdk/model/`, then re-run Step 2 and Step 3. Never edit `ts/` by hand — it gets overwritten.

That's the entire assessment.

## Conclusion

The website is confusing and full of marketing content, even on the pages titled "Documentation". A technical user would be lost and frustrated. The best material is in `AGENTS.md`, which is written for AI agents but is the most useful thing I found as a human.

1. The website is the documented entry point, but the real documentation is not there. Even `/sdk/docs` is marketing-shaped, and one page still used `.aon` where the current GitHub guide uses `.aontu`.
2. The clearest runbook is in `AGENTS.md`. Although it is framed for AI agents, it is the best human onboarding doc in the project, and the website never points humans to it.
3. The names are easy to confuse: `create-sdkgen` versus `sdkgen`, the `npm create @voxgig/sdkgen` command silently running `create-sdkgen`, and two overlapping tutorials in separate repos.
4. Small remark: The examples assume the OpenAPI spec is YAML rather than JSON, even though the tool accepts both.