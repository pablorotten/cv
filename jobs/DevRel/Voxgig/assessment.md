# VOXGIG assessment

## Task 1: build a SDK

Build an open-source SDK under the MIT License in your own GitHub or GitLab account, using the Voxgig SDK tools, and write a short report on your observations. The project remains your open-source work, you retain the copyright, and you are free to reference it for other work.

Please choose an API that does not already have an SDK in our open-source catalogue:
https://github.com/orgs/voxgig-sdk/repositories

You may use AI or build it manually, so long as you use the Voxgig SDK generator:
https://voxgig.com/sdk

I recommend an API from a SaaS company with a free trial, since you will need an API key to test fully. A personal or side project with an API is also a good choice.

Please time-box the human work to 30 minutes maximum. If that is not enough, or if you find issues or bugs, that is fine: include them in your report. We are very interested in your developer experience with the generator.

## Human journey

### Main page

Go to https://voxgig.com/sdk 

> [!NOTE]
> Nothing interesting.

> [!WARNING]
> Spoiler: ...Handing the build to an AI agent? The [agent guide](https://voxgig.com/sdk/agents) is the entry point written fo
> Goes to: https://voxgig.com/sdk/agents 
> That contains: Reading this as an agent? This page's markdown twin is at https://voxgig.com/sdk/agents.md
> And this https://voxgig.com/sdk/agents.md is ❤️fantastic❤️ It should be the home page


I go to https://www.voxgig.com/sdk/docs, I find those steps:

```
# Toolchain documentation

The toolchain is a pipeline of separately published packages. This section documents each of them, with every example taken from a public SDK the toolchain generated.

## The pipeline

| Stage |Done by |Produces |
|---|---|---|
| Describe | your OpenAPI 3 or Swagger 2 spec |the API as its authors wrote it, paths and schemas |
| Model | apidef |entities, operations, fields and flows, with the guide that records why |
| Shape | you, editing the model |the SDK surface you actually want: names, types, which operations exist |
| Generate | sdkgen |one SDK per target language, plus a CLI, an MCP server and generated docs |
| Verify | the generated offline suites |tests that run 
with no server and no credentials |
```

> [!NOTE]  
> - What is this pipeline? Is a "getting started" guide? feels like a marketing thing rather than a technical guide
> - "Toolchain documentation" title. I'm generating an SDK from an existing API, what does this to do with "Toolchain documentation"?
> - Why not here a clear "Steps to generate your SDK from an API"
> - "Describe step": Done openAPI 3 or Swagger 2. I understand this is a prerequisite, should be marked like that `prerequisite` instead of this weird step. It looks like the sdkgen can do it. Also, I know what is Swagger and openAPI but someone might not know. Links or short description doesn't hurt.
> - "Model done by apidef": Again No idea what is `apidef` and no linnks. I had to google it. And this is a voxgig tool so why not link it?
> - "Shape	you, editing the model": Not clear what is the goal of this stage. Like review what apidef generated? Not sure
> - We are on stage 3 and those are still pre-requisites to use the `sdkgen` tool, that it's the goal
> - "Generate	sdkgen" Finally!. But no idea what the command is


I go down this page and I see:

```
## Where to start
- Building an SDK for your own API: start at create-sdkgen.
- Working out what the generator can produce: sdkgen.
- The SDK has the wrong shape and you need to correct it: apidef.
- Extending the toolchain rather than using it: docgen, the worked example of a package.
```

> [!NOTE]
> How is this different to "The pipeline"? Again there're some random steps not sure what to do


Now I take a look to the page slowly, I see "The components" section
```
## The components 

Each is a separately published package with its own repository and its own release cycle. A new sibling ships as a package, not as a change to the generator.

### sdkgen
Turns the model into SDKs. The generator. It reads the model apidef produced and writes one idiomatic SDK per target language, each with the same operation pipeline, the same feature set, generated documentation, and an offline test suite.

Read the sdkgen documentation ➡️

### apidef
Turns a spec into a model. The front half. It reads an OpenAPI 3 or Swagger 2 spec and produces an internal model of entities, operations, fields and flows. It infers what the spec leaves implicit and records why it decided each thing.

Read the apidef documentation ➡️

### create-sdkgen

Scaffolds a project. The way in. One command turns an OpenAPI spec into a project with the model already built, the targets you asked for already added, and a generate script wired up. Start here unless you are working on the toolchain itself.

Read the create-sdkgen documentation ➡️

### docgen
Generates documentation targets. An sdkgen package rather than a separate tool. sdkgen defines a docs kind, a target whose destination is a documentation system rather than a language; docgen supplies the items for it.

Read the docgen documentation ➡️

### apigen
Not yet published. apigen has a repository on GitHub but no published package.

apigen on GitHub ➡️
```

> [!NOTE]
> What is this what are those tools?
> What's the difference between sdkgen and create-sdkgen
> At this point I'm lost, I don't know what to do

https://github.com/voxgig/sdkgen/blob/main/AGENTS.md Explains that:

`Building an SDK, not modifying the generator? If your goal is to produce an SDK for your own API — i.e. consume this tool rather than change it — start at create-sdkgen/AGENTS.md: the end-to-end spec → scaffold → generate → test → publish guide. This file is for working on the generator itself.`

This should be very clear in the top
--- 

I find this other tutorial on that page https://voxgig.com/sdk/docs/sdkgen#first-party-documentation:

```
Tutorial: generate your first SDK ➡️
```

That links to a [tutorial](https://github.com/voxgig/sdkgen/blob/main/docs/tutorial.md) 

## Notes

- Always assumes in exmpales openapi is yaml and not json format
 
### Am I dumb?

Not dumb. The docs are genuinely confusing, and it's not you. Concrete evidence:
- Two packages (create-sdkgen, sdkgen) with near-identical names, in separate repos, where npm's npm create @voxgig/sdkgen command silently runs the other one.
- A page titled "for AI agents" holds the clearest human runbook.
- The pipeline page names stages (Model, Generate) but not the commands or the packages that do them.
- Package-name-vs-CLI-name mismatches everywhere (@voxgig/sdkgen ↔ voxgig-sdkgen ↔ create-sdkgen).
- .aon vs .aontu extension churn mid-docs.
You spent 20 minutes untangling naming that a single "here's the one command, here's what each part does" paragraph would have solved. That's a documentation bug, not a you bug.
And here's the thing: this is the assessment. Richard isn't paying you for the SDK — it's 30 minutes of generator work. He's paying for exactly the observations you're making right now: "the entry point is confusing, here's where, here's the fix." You're already writing the report in your head.
Want to keep going and turn this frustration into the report? I can help you structure it as: (1) the confusion you hit, (2) each with a proposed fix, (3) the good parts. That's the deliverable.

## OK I'm done, I'll ask AI

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

Only if you have an API key, make a single live request to prove it works end to end. If you don't, skip — the offline tests already prove it.

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

That's the entire assessment. Two things I can do for you right now: pick an API, or run Step 1 against your `openapi.json` — do you have a spec file already?


## Conclusion

webpage is confusing and full of marketing content even in the pages with Documentation in the title. A technical user would be lost and frustrated. The dough is in agents.md that is meant to be ued for agents but it's actually the most interesting information for humans

1. The marketing site is the documented entry point, but the real documentation isn't there. Even /sdk/docs and /sdk/docs/create-sdkgen are marketing-shaped — stale (.aon), no runnable "start here" path.
2. The one page written clearly is written for the wrong audience. AGENTS.md — labelled "for AI agents" — is the best human onboarding doc in the whole project. The clearest runbook is hidden behind a repo file most humans won't open, because the site never says "the real guide is AGENTS.md."
3. The names defeat the reader. create-sdkgen vs sdkgen, @voxgig/sdkgen npm command launching @voxgig/create-sdkgen, two overlapping tutorials in two repos. Every step has a naming trap.