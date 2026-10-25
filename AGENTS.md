# Agent instructions

This repository owns shared Exynos 8890 resources: CPU topology, PSCI, GICv2,
the architectural timer, UFS controller ranges and ordered XNU patches. Board
memory, reserved regions, display, input, power and partition policy stay in
the device repository. Preserve existing source filenames, classes and symbols.

Read these UniXNU pages before editing:

1. [Porting](https://unixnu.com/porting/)
2. [SoC support](https://unixnu.com/porting/soc-support)
3. [Device trees](https://unixnu.com/porting/device-tree)
4. [Driver matching](https://unixnu.com/drivers/device-tree-matching)

Hardware values must be traceable to the stock G935F boot DTB or the vendor
kernel source pinned in `soc.toml`. Do not copy Exynos 8895 register values.
Select components by interface, hardware revision and OS ABI.

Run builds from the UniXNU checkout:

```sh
./unixnu defconfig hero2lte_defconfig -D ../UniXNU-hero2lte
./unixnu status --json -D ../UniXNU-hero2lte
./unixnu tree -D ../UniXNU-hero2lte
```

Report commands, results, required local inputs and hardware checkpoints.
Write concise English describing current behavior.
