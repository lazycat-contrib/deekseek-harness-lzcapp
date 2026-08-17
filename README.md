# DeepSeek Harness for LazyCat

This repository packages [DeepSeek Harness](https://www.deepseek.com/harness/) as a LazyCat LPK v2 application.

## Runtime

- Upstream image: `docker.io/1panel/deepseek-harness:0.1.0-rc.6`
- Target platform: `linux/amd64`
- Delivery: Docker Hub mirror (`docker.1ms.run` by default)
- Persistent data: `/lzcapp/var/data`
- Persistent workspace: `/lzcapp/var/workspace`

The deployment wizard exposes the administrator username and generates a random 20-character password by default. The browser inject automatically fills those credentials on the Harness login page.

## Automation

The scheduled workflow discovers future numeric `X.Y.Z-rc.N` image tags, builds a versioned GitHub Release asset, and publishes only to the MiaoMiao private store. The official LazyCat store is disabled.

Package ID: `community.lazycat.app.deepseek-harness`.

Configure these GitHub Secrets before running the workflow:

- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID` (optional for an existing store application)
- `PRIVATE_STORE_GROUP_CODES` (optional for private groups)

Organization Secrets must explicitly authorize this repository. A same-name repository Secret takes precedence.
