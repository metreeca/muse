# @metreeca/muse

[![npm](https://img.shields.io/npm/v/@metreeca/muse)](https://www.npmjs.com/package/@metreeca/muse)

AI tasks and shared services for [@metreeca/muse](https://github.com/metreeca/muse).

A consumer sets up a [@metreeca/gear](https://github.com/metreeca/gear) executor, binding the models a job relies on to
the implementations chosen for the run. The job's tasks then resolve each model through the locator, naming it by its
contract rather than importing a concrete client.

Binding a different implementation leaves the job unchanged: the same job runs against a live provider, against
recorded responses, or against any custom client honouring the same contracts.

# Installation

```shell
npm install @metreeca/gear  # the job executor
npm install @metreeca/muse  # this package
```

> [!IMPORTANT]
>
> Node.js 22 or later is required.

> [!WARNING]
>
> TypeScript consumers must use `"moduleResolution": "nodenext"/"node16"/"bundler"` in `tsconfig.json`.
> The legacy `"node"` resolver is not supported.

# Usage

| Module                 | Description                                |
|------------------------|--------------------------------------------|
| [@metreeca/muse][muse] | Model access contracts and shared services |

[muse]: https://metreeca.github.io/muse/modules/_metreeca_muse.index.html

# Support

- open an [issue](https://github.com/metreeca/muse/issues) to report a problem or to suggest a new feature
- start a [discussion](https://github.com/metreeca/muse/discussions) to ask a how-to question or to share an idea

# License

This project is licensed under the Apache 2.0 License –
see [LICENSE](https://github.com/metreeca/muse?tab=Apache-2.0-1-ov-file) file for details.
