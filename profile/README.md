<p align="center">
  <a href="https://embra.cloud/">
    <img src="https://raw.githubusercontent.com/embra-labs/.github/main/profile/cover.svg" alt="Embra — App hosting, with Postgres in mind." width="960" />
  </a>
</p>

<p align="center">
  <a href="https://embra.cloud/">Website</a> &nbsp;·&nbsp;
  <a href="https://embra.cloud/engineering/">Engineering</a> &nbsp;·&nbsp;
  <a href="https://github.com/embra-labs/.github/blob/main/docs/start-here.md">Start here (Tiếng Việt)</a> &nbsp;·&nbsp;
  <a href="https://embra.cloud/#join">Join alpha waitlist</a> &nbsp;·&nbsp;
  <a href="https://github.com/embra-labs/.github/blob/main/docs/changelog.md">Changelog</a> &nbsp;·&nbsp;
  <a href="mailto:hello@embra.cloud">Contact</a>
</p>

We're building an app hosting platform for teams in Vietnam, with Postgres at the heart of the deployment workflow.

**In development · Preparing closed alpha with manual onboarding by invitation.** See our [roadmap and evidence](https://embra.cloud/#trang-thai). Joining the waitlist does not grant immediate access; the opening date is not set.

M1 builds the CLI, container-image deployment, Postgres, and migration foundations. M2 continues the product flow illustrated on the website. The invitation will confirm which capabilities are ready.

### What we're building

Shipping an app means changing code **and** the data it depends on. We're designing Embra around three priorities:

- **Understand database changes before deployment.** Rehearse migrations and surface their impact before applying them.
- **Keep consequential changes under your control.** Make approval an explicit part of the workflow.
- **Make recovery decisions clear.** Show what can be restored, and what data could be lost.

Explore the [interactive concept demo](https://embra.cloud/) on our website. It illustrates the intended workflow; it is not a live production deployment.

### Engineering notes

[Backfilling 8 million rows: correctness passed, latency did not](https://embra.cloud/engineering/backfill-8m/) (Tiếng Việt). A lab report on transactional checkpoints, interrupted backfills, and p99 measurement—with figures, aggregate data, and measurement limits.

Try the [runnable backfill demo](https://github.com/embra-labs/backfill-demo): one command, two crash boundaries, and negative controls that catch skipped/repeated work. A separate 1,000-row teaching fixture, not the article’s benchmark.

### Explore Embra

| Repository | What you'll find |
| :--- | :--- |
| [backfill-demo](https://github.com/embra-labs/backfill-demo) | Runnable PostgreSQL crash/resume example with CI and negative controls. |
| [cli](https://github.com/embra-labs/cli) | Home of the Embra command-line client. In development; no public release yet. |
| [embra-cloud](https://github.com/embra-labs/embra-cloud) | Source for the Embra website. |

Building an app with Postgres? [Tell us about your project →](https://embra.cloud/#join)
