# How to use

TL;DR; To use the j&s-soft default preset, extend your Renovate configuration with `github>js-soft/renovate-config`.

## Detailed instructions

> [!CAUTION]
> If you want to allow Renovate to automatically merge dependency updates, your repository needs to have at least one status check (aka test pipeline) configured. If you don't have any status checks and are not planning to introduce any, you can set the `ignoreTests` property to `true` (refer to https://docs.renovatebot.com/key-concepts/automerge/#absence-of-tests for details). But keep in mind that this will allow Renovate to automatically merge PRs without any checks, even if you add status checks in the future. It's recommended to have at least some small check (e.g. tsc, linting, formatting-checks, ...) in place.

To enable Renovate in your repository, the following steps are required:

1.  Create a file named `renovate.json` in the `.github` folder
2.  Add the following content:

    ```json
    {
      "$schema": "https://docs.renovatebot.com/renovate-schema.json",
      "extends": ["github>js-soft/renovate-config"],
      "reviewers": ["<comma>", "<separated>", "<list>", "<of>", "<reviewers>"]
    }
    ```

3.  Replace the list of reviewers with the GitHub usernames of the people you want to be notified about new PRs created by Renovate.

Now all you have to do is wait for the next scheduled run of Renovate (by default, this is every Monday morning).

> [!NOTE]
> Keep in mind that this only updates dependencies. If your repository contains a deliverable, you still have to build new releases regularly.
