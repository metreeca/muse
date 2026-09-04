# @metreeca/muse

Ready-made tasks and shared services for AI jobs.

**@metreeca/muse** brings ready-made [@metreeca/flow](https://github.com/metreeca/flow) tasks for putting model work
into a pipeline: prompting a model, extracting structure from free text, embedding content for retrieval. The tasks run
under the [@metreeca/gear](https://github.com/metreeca/gear) job executor, which supplies the shared services they draw
on.

- **Ready-Made Tasks**: prompting, extraction and embedding, chaining alongside any other task
- **Shared Services**: the model clients, credentials and response caches a run needs, built on demand and released as
  it ends
- **Custom Bindings**: a stubbed, throttled or recorded model swapped in for a run, leaving the job untouched
- **Minimal Footprint**: one package per model provider, each pulling in only the SDK that provider needs

> [!IMPORTANT]
>
> Pipelines are server-side workloads targeting [Node.js](https://nodejs.org/) 22 or later, relying on facilities such
> as the filesystem, the process environment and `fetch`. The packages are not intended for the browser.

# Installation

```shell
npm install @metreeca/gear             # job executor and shared services
npm install @metreeca/muse             # model access contracts and shared services
npm install @metreeca/muse-<provider>  # task package, one per model provider
```

> [!WARNING]
>
> TypeScript consumers must use `"moduleResolution": "nodenext"/"node16"/"bundler"` in `tsconfig.json`.
> The legacy `"node"` resolver is not supported.

Install the core package, then add a task package for each model provider the pipeline reaches. Provider packages are
self-contained leaves, each pulling in only the SDK its own provider needs. The job executor comes from
[@metreeca/gear](https://github.com/metreeca/gear), which the core package pulls in transitively; install it directly
to set up and run a job.

| Package                 | Description                  |
|-------------------------|------------------------------|
| [@metreeca/muse]        | AI tasks and shared services |
| [@metreeca/muse-google] | Google model connectors      |

[@metreeca/muse]: https://metreeca.github.io/muse/modules/_metreeca_muse.html

[@metreeca/muse-google]: https://metreeca.github.io/muse/modules/_metreeca_muse-google.html

# Usage

> [!NOTE]
>
> Each package documents its own API in its README and API reference; for complete coverage, see the
> [API reference](https://metreeca.github.io/muse/).

# Support

- open an [issue](https://github.com/metreeca/muse/issues) to report a problem or to suggest a new feature
- start a [discussion](https://github.com/metreeca/muse/discussions) to ask a how-to question or to share an idea

# License

This project is licensed under the Apache 2.0 License –
see [LICENSE](https://github.com/metreeca/muse?tab=Apache-2.0-1-ov-file) file for details.
