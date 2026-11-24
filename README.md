# VC4QI

**Verifiable Credentials for Quality Infrastructure** is research software for a
practical question: when a verifier receives a credential, what evidence justifies
relying on it?

[![CI](https://github.com/QI-Data-Lab/VC4QI/actions/workflows/ci.yml/badge.svg)](https://github.com/QI-Data-Lab/VC4QI/actions/workflows/ci.yml)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)

> **Try it:** [Open the browser demonstrator](https://qi-data-lab.github.io/VC4QI/demo/) ·
> [Follow the reference-material story](https://qi-data-lab.github.io/VC4QI/demo/rm/) ·
> [Browse four worked examples](https://qi-data-lab.github.io/VC4QI/demo/examples/) ·
> [Read the project overview](https://qi-data-lab.github.io/VC4QI/)

The demonstrator runs the repository's evaluator in your browser using signed test
credentials. Nothing is fetched from a server. Authorities, keys and grants in the
examples are fictional; they do not claim real accreditation or external endorsement.

## Explore the demonstrator

| Start here | What you can explore |
| --- | --- |
| [**Reference-material story**](https://qi-data-lab.github.io/VC4QI/demo/rm/) | Follow a certified arsenic value through its chain of authority, then test how trust, status, scope and conformity affect the verifier's decision. |
| [**Four worked examples**](https://qi-data-lab.github.io/VC4QI/demo/examples/) | Compare reference material, calibration certificates, a GS mark and an experimental product passport. Change the verifier's trust settings or test altered and missing evidence. |
| [**GS certification story**](https://qi-data-lab.github.io/VC4QI/demo/gs/) | Explore the product-safety credential chain on an actor board, with scenarios involving revocation, withdrawal and changed product data. |

Each answer is **established**, **contradicted** or **not established**. Missing or
unsupported evidence never counts as a pass. The verifier chooses the profile and trust
anchors; a credential does not create its issuer's authority.

## What the project provides

- A standards-first reliance evaluator for reference-material, calibration and GS
  certification bindings.
- A canonical TypeScript implementation and a Python mirror, exercised against signed
  fixtures and shared semantics.
- A browser demonstrator using the same evaluator, including DPP examples.
- Documentation of the reliance model, credential bindings, API and known limitations.

This is a research reference implementation, not a verifier service or trust registry.
See [current status and limitations](docs/status.md) for what is implemented.

## Find your way around

| I want to... | Go to |
| --- | --- |
| Understand the reliance rules | [Reliance model](docs/model.md) |
| Read the scenarios | [Use cases](docs/use-cases.md) |
| Check implementation status and open limitations | [Status](docs/status.md) |
| Use the evaluator API | [API](docs/api.md) |
| See how credential families are interpreted | [Bindings](docs/bindings.md) |
| Navigate the source and evaluator design | [Architecture](docs/architecture.md) |
| Start with the documentation guide | [Documentation index](docs/index.md) |
| Contribute or run project checks | [Contribution guide](CONTRIBUTING.md) |

The [acceptance ledger](docs/acceptance-ledger.csv) records expected outcomes and
evidence. The [architecture decisions](docs/adrs/README.md) explain key design choices.

## Run locally

Install Node 20, pnpm 10.15.1, Python 3.12 and uv 0.12.17, then install dependencies
and run the core checks:

```bash
pnpm install --frozen-lockfile
uv sync --locked --all-packages --extra dev
pnpm -r build
pnpm -C packages/core-ts test
uv run --locked --all-packages --extra dev pytest packages/core-py/tests
```

To build the demonstrator, run `pnpm -C apps/demonstrator build`. To build the complete
site locally, run `pnpm docs:build` and open `_site/demo/index.html`. See
[CONTRIBUTING](CONTRIBUTING.md) for all checks and repository guidance.

## Attribution and citation

VC4QI was created by **Mehran Monavari**. If you use it in a publication, please cite
both the associated paper and the software. Citation formats and BibTeX are on the
[Cite page](https://qi-data-lab.github.io/VC4QI/docs/cite.html) and in [CITATION.cff](CITATION.cff).

### Paper

> Mehran Monavari (2026). *Verifiable Trust Chains for Quality Infrastructure: A
> Verification Framework over W3C Verifiable Credentials.*

The venue and DOI will be added when they are available.

### Software

> Mehran Monavari (2026). *VC4QI: Verifiable Credentials for Quality Infrastructure*,
> version 0.4.0 [Software]. Zenodo. <https://doi.org/10.5281/zenodo.23979553>

To cite the latest version instead of 0.4.0, use the concept DOI
<https://doi.org/10.5281/zenodo.20612364>.

<details>
<summary>Copyable BibTeX for both citations</summary>

```bibtex
@unpublished{monavari2026trustchains,
  author = {Monavari, Mehran},
  title  = {Verifiable Trust Chains for Quality Infrastructure: A Verification
            Framework over {W3C} Verifiable Credentials},
  year   = {2026},
  note   = {Venue and DOI to be added}
}

@software{monavari2026vc4qi,
  author    = {Monavari, Mehran},
  title     = {{VC4QI}: Verifiable Credentials for Quality Infrastructure},
  version   = {0.4.0},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.23979553},
  url       = {https://doi.org/10.5281/zenodo.23979553}
}
```

</details>

Authorship and copyright are separate: Mehran Monavari is the sole author, and the
copyright notice reads "VC4QI Contributors" (see [NOTICE](NOTICE)). Citation is
requested, not required by the licenses.

## License

Code is licensed under [Apache-2.0](LICENSE); documentation is licensed under
[CC BY 4.0](LICENSE-docs). Attribution notices are in [NOTICE](NOTICE).
