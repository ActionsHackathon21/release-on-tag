Release new version on tag
===
*Bonus: Also notify your followers on every update!*

*This project follows the DEV.to [#ActionsHackathon21](https://dev.to/devteam/join-us-for-the-2021-github-actions-hackathon-on-dev-4hn4) hackathon.*

Use GitHub Actions and Workflows to build and release your application on every release tag.

![Screenshot](https://github.com/ActionsHackathon21/release-on-tag/raw/main/screenshot.png)

Then send an announcement to your Telegram channel about the new release

![Telegram](https://github.com/ActionsHackathon21/release-on-tag/raw/main/screenshot2.png)


Check the complete workflow here ([release-on-tag.yml](.github/workflows/release-on-tag.yml))

## Actions used
- **[actions/checkout@v2](https://github.com/actions/checkout)** To checkout the source code from the repository
- **[actions/cache@v2](https://github.com/actions/cache)** To cache the dependencies, allow us to re use them for future builds
- **[marvinpinto/action-automatic-releases@latest](https://github.com/marvinpinto/action-automatic-releases)** To release your build to Github Release page

(Also **[actions/setup-node@v2](https://github.com/actions/setup-node)** for setup nodejs, although it's not required)

## Configurations
- You can config the release tag prefix, with `on.push.tags` key.
- To send announcement to Telegram, you need to configure the workflow using following steps:
    - Talk with Telegram's [@BotFather](https://t.me/BotFather) to create a new bot if you don't have one. We will use this bot to send messages to the Telegram channel. He will give you the **token access the HTTP API**.
    - On your Telegram channel, grant admin permissions to the bot.
    - Set the `TELEGRAM_CHANNEL` variable.
    - Add the `TELEGRAM_BOT_TOKEN` secret (using the token access above) into your repository secret (**Settings** > **Secrets** > **New repository secret**)

## Flows
In this repository, I use a sample [NextJS](https://nextjs.org/) to demonstrate. However you can change the workflow a bit to fit your project.

- Use **[actions/checkout@v2](https://github.com/actions/checkout)** to checkout source code from the repository
- Use **[actions/setup-node@v2](https://github.com/actions/setup-node)** to setup nodejs
- Use **[actions/cache@v2](https://github.com/actions/cache)** to cache dependencies (`node_modules` and `.yarn` directories)
- Install dependencies with `yarn`
- Run tests
- Build application
- Prepare release build files
- Release the prepared files into Github Release
- Send an announcement to the specified Telegram channel
