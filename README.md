# action-aikido-scan

This action setup [Aikido](https://help.aikido.dev/doc/setting-up-image-scanning-with-local-scanner/doc3D3U3PYFL) CLI and allows automatic scanning images.

## Input

```yaml
inputs:
  arch:
    description: |
      defines the architecture of the runner
      default is: linux_X86_64
      accepts: linux_X86_64 | darwin_ARM64
    default: linux_X86_64
  api_key:
    description: |
      the API Key genererated in aikido
    required: true
  image_name:
    description: |
      name of your image in the local repository
    required: true
```

### Usage

```yaml
name: Pull Request
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
  workflow_dispatch:

jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - name: Scan
        uses: gusfune/aikido-scanner@1.0.19
        with:
          api_key: ${{ secrets.AIKIDO_API_KEY }}
          arch: linux_X86_64
          image_name: hello
```
