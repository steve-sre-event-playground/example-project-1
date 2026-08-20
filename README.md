# example-project-1
Pretending to be a project repo, will contain actual code that builds things

## Pipeline

`.github/workflows/pipeline.yml` is manually triggered (`workflow_dispatch`)
and pretends to build and deploy the app to a chosen environment. Once
"deployed" it calls the `notify-deployment` action from
[`shared-workflows-actions`](https://github.com/steve-sre-event-playground/shared-workflows-actions)
to emit a "just deployed" event to
[`steve-event-handler`](https://github.com/steve-sre-event-playground/steve-event-handler).

Requires the `SRE_EVENTMANAGER_CLIENT_SECRET` repo secret to authenticate the
cross-repo `workflow_dispatch` call.
