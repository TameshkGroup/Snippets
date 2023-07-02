## Monitoring
Install `intel-gpu-tools` and `nvtop`

```bash
intel_gpu_top
```
```bash
nvtop
```

## Enabling modesetting

```bash
nano /etc/X11/xorg.conf.d/20-intel.conf
```

add the following lines:
```bash
Section "Device"
  IdentifieR  "Intel Graphics"
  Driver      "modesetting"
  Option      "TearFree"  "true"
  Option      "DRI"  "iris"
ENDSection
 
```

## Enable GuC / HuC firmware loading
Offloading some media decoding functionality from the CPU to the HEVC/H.265 micro (µ) Controller (HuC). Only applicable if using `intel-media-driver` for hardware video acceleration. Introduced with `Gen9`.

```bash
nano /etc/modprobe.d/i915.conf
```

```bash
options i915 enable_guc=2
```
