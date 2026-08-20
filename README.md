# example-project-1
Pretending to be a project repo, will contain actual code that builds things

## Pipeline

`.github/workflows/pipeline.yml` is manually triggered (`workflow_dispatch`)
and pretends to build and deploy the app to a chosen environment. The build
step also generates a build-provenance attestation (`actions/attest-build-provenance`)
for the fictional build artifact, so its authenticity can later be verified
by other repos (see `steve-sbom-handler`). Once "deployed" it calls the
`notify-deployment` action from
[`shared-workflows-actions`](https://github.com/steve-sre-event-playground/shared-workflows-actions)
to emit a "just deployed" event (including the artifact name/digest) to
[`steve-event-handler`](https://github.com/steve-sre-event-playground/steve-event-handler).

Requires the `SRE_EVENTMANAGER_APP_ID` and `SRE_EVENTMANAGER_PRIVATE_KEY` repo
secrets, used to mint a short-lived installation token for the
`example-eventmanager` GitHub App, which authenticates the cross-repo
`workflow_dispatch` call. A raw OAuth client secret can't be used here - it
only supports interactive user login flows, not Actions API calls.
