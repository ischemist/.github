### the grammar

every label is namespaced with a prefix that answers a fundamental question about the issue.

- `type/`: **what** is it?
- `status/`: **where** is it in the workflow?
- `priority/`: **when** should it be done?
- `scope/`: **which part** does it affect?
- `community/`: **who** is this for?

an issue should have exactly one `type`, one `status`, and one `priority` label. it can have multiple `scope` labels. `community` labels are optional.

### the system

#### `type/` — the nature of the issue

| label           | description                                                   |
| --------------- | ------------------------------------------------------------- |
| `type/bug`      | something is broken or not working as intended.               |
| `type/feature`  | a new capability or enhancement for the user.                 |
| `type/refactor` | internal code quality improvement. no user-facing changes.    |
| `type/docs`     | improvements or additions to documentation.                   |
| `type/chore`    | maintenance work (e.g., updating dependencies, ci/cd config). |
| `type/security` | a vulnerability or security-related concern.                  |

#### `status/` — the workflow state

| label                  | description                                              |
| ---------------------- | -------------------------------------------------------- |
| `status/needs-triage`  | this issue has not yet been reviewed by a maintainer.    |
| `status/needs-info`    | more information is required from the issue reporter.    |
| `status/ready-for-dev` | triaged and ready to be picked up for implementation.    |
| `status/in-progress`   | this issue is actively being worked on.                  |
| `status/in-review`     | a pull request has been opened and is awaiting review.   |
| `status/blocked`       | progress is blocked by another issue or external factor. |

#### `priority/` — the urgency

| label                 | description                                                    |
| --------------------- | -------------------------------------------------------------- |
| `priority/0-critical` | MUST be dealt with immediately. production is on fire.         |
| `priority/1-high`     | important and should be prioritized in the current work cycle. |
| `priority/2-medium`   | default priority for most issues.                              |
| `priority/3-low`      | nice-to-have, can be worked on when time permits.              |

#### `scope/` — the affected area

| label            | description                                                                        |
| ---------------- | ---------------------------------------------------------------------------------- |
| `scope/domain`   | the core logic, abstractions, and internal workings of the package or application. |
| `scope/backend`  | affects the backend api or server-side logic.                                      |
| `scope/ml-model` | related to the core machine learning model architecture or training.               |
| `scope/data`     | involves data processing, pipelines, or datasets.                                  |
| `scope/ui`       | changes to react components, css, and visual presentation.                         |
| `scope/ux`       | affects user flow, interaction design, and overall experience.                     |
| `scope/auth`     | related to user authentication or authorization.                                   |
| `scope/ci-cd`    | affects github actions, deployment, or build processes.                            |
| `scope/testing`  | related to unit, integration, or e2e tests.                                        |

#### `community/` — external engagement

| label                        | description                                                          |
| ---------------------------- | -------------------------------------------------------------------- |
| `community/good-first-issue` | good for newcomers who want to contribute.                           |
| `community/help-wanted`      | seeking help from the community on this issue.                       |
| `community/needs-discussion` | requires a design discussion or broader input before implementation. |

---

### workflow and philosophy

1.  **ingestion:** a new issue is filed. it automatically gets `status/needs-triage`. your job as maintainer is to keep this queue at zero.
2.  **triage:** you assess the issue.
    - is it valid? if not, close it. do not use a label. github has close reasons (`duplicate`, `wontfix`, `not planned`). use them.
    - if valid, add `type/`, `priority/`, and `scope/` labels.
    - if it's ready for work, change `status/needs-triage` to `status/ready-for-dev`.
    - if you need more info, change it to `status/needs-info`.
3.  **execution:** a contributor picks up an issue and changes its status to `status/in-progress`. when a pr is opened, it becomes `status/in-review`.
