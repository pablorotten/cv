# Voxgig assessment notes - Task 1: Build an SDK and write a report

> [!NOTE]
> Environment disclaimer: I completed this assessment on **Windows 11**, AI-assisted with **Muse Spark 1.3 via OpenCode**.

This task asks you to build an open-source SDK under the MIT License in your own GitHub or GitLab account, using the Voxgig SDK tools, and write a short report on your observations. The project remains your open-source work, you retain the copyright, and you are free to reference it for other work.

Please choose an API that does not already have an SDK in our open-source catalogue:
https://github.com/orgs/voxgig-sdk/repositories

You may use AI or build it manually, so long as you use the Voxgig SDK generator:
https://voxgig.com/sdk

I recommend an API from a SaaS company with a free trial, since you will need an API key to test fully. A personal or side project with an API is also a good choice.

Please time-box the human work to 30 minutes maximum. If that is not enough, or if you find issues or bugs, that is fine: include them in your report. We are very interested in your developer experience with the generator.

There is no fixed deadline; about one calendar week is a useful guide.

Once this task is complete, we will send the second task under the same conditions.
## Human journey

This is my personal journey to generate an SDK, starting from the website

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

## Robot journey

Those are the steps AI generated to complete the assessment. It is very clear what I have to do.

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

> [!NOTE]
> It merges the installation of `@voxgig/create-sdkgen` with the execution in one single command


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

## Building the SDK in Windows

I picked [The Movie Database (TMDB)](https://developer.themoviedb.org/) to generate the SDK from. Spec: https://developer.themoviedb.org/openapi/tmdb-api.json

Next, I follow the [Quickstart](https://github.com/voxgig/create-sdkgen/tree/main#quickstart).

```sh
# 1. Scaffold a project from your OpenAPI 3 spec
create-sdkgen tmdb -d ./tmdb-api.json -o ./tmdb-sdk

# 2. Add the languages you want + offline test mode
cd tmdb-sdk/.sdk
npx voxgig-sdkgen target add ts py go
npx voxgig-sdkgen feature add test

# 3. Generate the SDKs (builds the .sdk sources, then runs the generator)
npm run generate

# 4. Verify
cd ../ts && npm install && npm run build && npm test
```

### Some comments

> [!WARNING]
> **Feedback:** The README [Quickstart](https://github.com/voxgig/create-sdkgen/tree/main#quickstart) and [AGENTS.md](https://github.com/voxgig/create-sdkgen/blob/main/AGENTS.md) have no **Prerequisites** section. The missing prerequisites are:
> - use Node 24+
> - install `create-sdkgen`
> ```sh
> nvm install 24
> nvm use 24
> npm install -g @voxgig/create-sdkgen 
> ```

### Bugs found

While actually running the steps on Windows I hit two errors and could not finish the generation. Both turn out to be **known, open issues filed by the maintainer**, so I am not doing anything wrong: the Windows path of the tool is currently broken.

#### Bug 1: `spawn npm ENOENT`

`create-sdkgen tmdb -d ./tmdb-api.json -o ./tmdb-sdk` fails at the install step:

```
INFO: create/jostraca generate-install running npm install in .\tmdb-sdk\.sdk
Voxgig Create SDK Error: Failed to start npm: spawn npm ENOENT
```

Known issue: [#58: Fix npm process launching in the generated scaffold on Windows](https://github.com/voxgig/create-sdkgen/issues/58)

#### Bug 2: `api/api-info.aontu` source not found

After installing the dependencies manually, `npm run generate` fails during the model build:

```
ERROR: model run-build build
  [aontu/multisource_not_found]: source not found: api/api-info.aontu
  --> .sdk\model\sdk.aontu:13:1
```

Known issue: [#62: Bare includes in the scaffold's model and test files fail to resolve, notably on Windows](https://github.com/voxgig/create-sdkgen/issues/62)


### Workaround: Tried with WSL

I repeated the [Quickstart](https://github.com/voxgig/create-sdkgen/tree/main#quickstart) in WSL, and the pipeline completed. `npm install` succeeded, `npm run generate` parsed the OpenAPI spec and generated the TypeScript SDK. `apidef` reported 103 entities from 148 paths, but marked the build partial with 13 selector-collision warnings; `sdkgen` also warned that some generated flow steps were unreachable.

### Offline test result

`npm test` completed with **908 tests: 800 passed, 0 failed, 108 skipped** (duration: about 4 minutes). These are the generated offline tests; they use a mock and do not by themselves test requests against TMDB.

### Test the SDK against the API

> [!NOTE]
> TMDB's OpenAPI spec marks `Authorization` as a bearer credential, but passing the raw Read Access Token as `apikey` returned `401 Invalid API key`. Prefixing it with `Bearer ` fixed authentication. The generated client did not add this prefix automatically. With the prefix, `GET /3/authentication` returned `200`, and the `Movie().load()` and `Movie().list()` entity calls returned live movie data.

Set the API key in PowerShell:

```powershell
$env:TMDB_APIKEY = "..."
```

I wrote a small script in the `tmdb-sdk\ts` folder:
```ts
import { TmdbSDK } from './dist/TmdbSDK.js'

const client = new TmdbSDK({ apikey: 'Bearer ' + process.env.TMDB_APIKEY })

// Test authentication
const res = await client.direct({ path: '/3/authentication', method: 'GET' })
console.log('ok:', res.ok, 'status:', res.status)
console.log(JSON.stringify(res.ok ? res.data : res.err, null, 2).slice(0, 1200))

// Test entities
const movie = await client.Movie().load({ id: 550 })
console.log('load:', movie.data().title, '|', movie.data().release_date, '| ★', movie.data().vote_average)

// Test search
const found = await client.Movie().list({ query: 'Fight Club' })
console.log('search hits:', found.length, '| first:', found[0]?.data?.().title)
```

Run it in PowerShell:
```powershell
node .\live-check.mjs
```

✅ It worked!

```
ok: true status: 200
{
  "success": true
}
load: Fight Club | 1999-10-15 | ★ 8.438
search hits: 20 | first: Fight Club
PS C:\Users\pablo\DEV\projects\tmdb-sdk\ts
```


## Conclusion

The website is confusing and full of marketing content, even on the pages titled "Documentation". A technical user would be lost and frustrated. The best material is in `AGENTS.md`, which is written for AI agents but is the most useful thing I found as a human.

1. The website is the documented entry point, but the real documentation is not there. Even `/sdk/docs` is marketing-shaped, and one page still used `.aon` where the current GitHub guide uses `.aontu`.
2. The clearest runbook is in `AGENTS.md`. Although it is framed for AI agents, it is the best human onboarding doc in the project, and the website never points humans to it.
3. The names are easy to confuse: `create-sdkgen` versus `sdkgen`, the `npm create @voxgig/sdkgen` command silently running `create-sdkgen`, and two overlapping tutorials in separate repos.
4. Small remark: The examples assume the OpenAPI spec is YAML rather than JSON, even though the tool accepts both.
5. The [Quickstart](https://github.com/voxgig/create-sdkgen/tree/main#quickstart) is broken on Windows.
6. All the other small issues I found were easily fixed with the help of small model