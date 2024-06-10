The package name in the `go.mod` should be the same as the `git repo url`.


- `go.mod` file:

```go
module exampleUrl.com/name/repo
```

- Add git tag:

```bash
git tag v0.0.5
```

- Push the git tag:

```bash
git push origin v0.0.5
```

- Set the go env (just for fish):
```bash
set -Ux GOPRIVATE exampleUrl.com/name/repo
```

or 

```bash
set -Ux GOPRIVATE exampleUrl.com/name/*
```

- To add the library in your target go repostory: 

```bash
go get exampleUrl.com/name/repo
go get exampleUrl.com/name/repo@v0.0.5
```
