<p align="center">
  <a href="https://embra.cloud/">
    <img src="https://raw.githubusercontent.com/embra-labs/.github/main/profile/cover.svg" alt="Embra — App hosting, with Postgres in mind." width="960" />
  </a>
</p>

<p align="center">
  <a href="https://embra.cloud/">Website</a> &nbsp;·&nbsp;
  <a href="https://embra.cloud/engineering/">Engineering</a> &nbsp;·&nbsp;
  <a href="https://github.com/embra-labs/.github/blob/main/docs/start-here.md">Start here (Tiếng Việt)</a> &nbsp;·&nbsp;
  <a href="https://embra.cloud/bang-gia/">Pricing</a> &nbsp;·&nbsp;
  <a href="https://github.com/embra-labs/.github/blob/main/docs/changelog.md">Changelog</a> &nbsp;·&nbsp;
  <a href="mailto:hello@embra.cloud">Contact</a>
</p>

App and PostgreSQL hosting for developers and small teams in Vietnam, on servers in Ho Chi Minh City: deploy from GitHub, follow your app, and keep your database recoverable in one project.

If the person writing code is also configuring servers and handling deployments, Embra is designed to bring that work into one workflow. Database review and recovery preparation are part of it.

**Paid beta since 25 October 2026.** Production apps are accepted within each plan's limits, with direct onboarding for every customer and no SLA yet. Plans start at 249,000 VND per project per month: see [pricing](https://embra.cloud/bang-gia/).

The beta includes deploys from GitHub through the dashboard, a dedicated Postgres with migration review, continuous backup with point-in-time restore, workers, cron, file buckets, custom domains, logs and metrics. The CLI and an MCP server (`embra mcp`, where agents can propose but never approve) are coming to a public release soon. Queues, auth, email and realtime are not available yet.

### What we're building

Shipping an app means changing code **and** the data it depends on. We're designing Embra around the full deployment workflow:

- **Build and deploy the app.** Configure environments, inspect build logs, and follow release history alongside Postgres.

- **Understand database changes before deployment.** Rehearse migrations and surface their impact before applying them.
- **Keep consequential changes under your control.** Make approval an explicit part of the workflow.
- **Make recovery decisions clear.** Show what can be restored, and what data could be lost.

The [interactive demo](https://embra.cloud/#stage) on our website illustrates the workflow; it does not run on a live app.

### Engineering notes

[Backfilling 8 million rows: correctness passed, latency did not](https://embra.cloud/engineering/backfill-8m/) (Tiếng Việt). A lab report on transactional checkpoints, interrupted backfills, and p99 measurement—with figures, aggregate data, and measurement limits.

Try the [runnable backfill demo](https://github.com/embra-labs/backfill-demo): one command, two crash boundaries, and negative controls that catch skipped/repeated work. A separate 1,000-row teaching fixture, not the article’s benchmark.

### Who is building it?

[Hoàng Xuân](https://github.com/hxuan190) builds and supports Embra. Read the [founder’s note](https://embra.cloud/#nguoi-lam) or review [data, recovery, and support questions](https://embra.cloud/#hoi-dap).

### Explore Embra

| Repository | What you'll find |
| :--- | :--- |
| [backfill-demo](https://github.com/embra-labs/backfill-demo) | Runnable PostgreSQL crash/resume example with CI and negative controls. |
| [cli](https://github.com/embra-labs/cli) | Home of the Embra command-line client. No public release yet. |
| [embra-cloud](https://github.com/embra-labs/embra-cloud) | Source for the Embra website. |

Building an app with Postgres? [See pricing →](https://embra.cloud/bang-gia/)
