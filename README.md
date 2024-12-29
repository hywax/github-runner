# Self-Hosted Runner

A self-hosted runner for GitHub Actions.

## Usage

```yaml
services:
  runner:
    image: ghcr.io/hywax/github-runner # or replace with your own image 
    restart: always
    environment:
      - REPO=<owner>/<repo>
      - REG_TOKEN=<reg-token-for-self-hosted-runner>
      - NAME=<runner-name>
    deploy:
      mode: replicated
      replicas: 2
      resources:
        limits:
          cpus: '0.5'
          memory: 512M
        reservations:
          cpus: '0.4'
          memory: 256M
```

## Configuration

The following environment variables are required:

| ENV         | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| `REPO`      | The GitHub repository to register the runner                                          |
| `REG_TOKEN` | The registration token for the self-hosted runner from the GitHub repository settings |
| `NAME`      | The name of the self-hosted runner.                                                   |

## License

This is open-sourced software licensed under the [MIT license](LICENSE).
