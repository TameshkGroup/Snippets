

## Command to get top pods using docker (clean output)
```bash
docker stats --no-stream --format "table {{.Name}}\t{{.CPUPerc}}\t{{.MemUsage}}" | sed 's/k8s_//g' | sed 's/[0-9a-f]\{8\}-[0-9a-f]\{4\}-[0-9a-f]\{4\}-[0-9a-f]\{4\}-[0-9a-f]\{12\}_//g' | sed 's/_[0-9a-f]\{32\}_//g' | sort -h -k 3 | grep -v POD_
```
> Also web can append its function to .zshrc

```bash
function pods () {
  docker stats --no-stream --format "table {{.Name}}\t{{.CPUPerc}}\t{{.MemUsage}}" | sed 's/k8s_//g' | sed 's/[0-9a-f]\{8\}-[0-9a-f]\{4\}-[0-9a-f]\{4\}-[0-9a-f]\{4\}-[0-9a-f]\{12\}_//g' | sed 's/_[0-9a-f]\{32\>
}
```

## Change default namespace with kubectl 

```bash
kubectl config set-context --current --namespace=<namespace>
```
