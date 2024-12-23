# Action Golang with cache

Composite GitHub Action combining a perfect pairing of [useblacksmith/setup-go](https://github.com/useblacksmith/setup-go) with [useblacksmith/cache](https://github.com/useblacksmith/cache) for caching of both Golang module and build caches.

## Configuration

```yaml
- name: Setup Golang
  uses: Drafteame/go-cache-action@main
  with:
    go-version: 1.22.7 # go version
    go-version-file: go.mod # Path to go.mod file, will determine Golang version.
    cache-key-suffix: suffix # Optional cache key suffix


```
### Outputs

| Output     | Description                                       |
|------------|---------------------------------------------------|
| **build-cache-path**  | Golang build cache path. |
| **module-cache-path**  | Golang module cache path. |
| **cache-key**  | Cache key holding Golang build and module cache paths. |

## Usage

```yaml
steps:
  - name: Setup Golang with cache
    uses: Drafteame/go-cache-action@main
    with:
      go-version: 1.22.7

```

or better yet, use `go-version-file` for version selection:

```yaml
steps:
  - name: Setup Golang with cache
    uses: Drafteame/go-cache-action@main
    with:
      go-version-file: go.mod
```

Action correctly saves/restores **build** and **module** cache paths for Linux, macOS _and_ Windows runners.
