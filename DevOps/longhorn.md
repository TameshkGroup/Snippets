
Fix longhorn error `Volume is already exclusively attached to one node and can't be attached to another`

```bash
kubectl get volumeattachment | grep pvc-c7155aa8-282a-461f-b1fb-4260b0687b69
kubectl delete volumeattachment csi-f12fdf2abf305183d7eba30b4012c97a33d33dc0b61612756ec330b0f32901e7
```
