# UniXNU Exynos 8890 support

Shared Samsung Exynos 8890 (S5E8890) support for UniXNU: CPU topology, PSCI,
GICv2, the 26 MHz architectural timer and the UFS controller ranges. Board
memory, reserved regions, display, input, power and partition policy stay in
the device repository.

| Path | Contents |
| --- | --- |
| `soc.toml` | SoC profile and component selection |
| `configs/exynos8890.config` | Kernel configuration fragment |
| `dts/exynos8890.dtsi` | Shared CPU, PSCI, GIC and timer resources |
| `patches/xnu/series` | Ordered SoC patches |
| `kits/` | Shared platform operations |

Hardware values come from the stock `G935FXXS6ESI4` boot DTB captured from the
SM-G935F unit and are cross-checked against the HeroGrace Exynos 8890 kernel
source recorded in `soc.toml`. The stock tree labels cluster 0
(MPIDR `0x0`-`0x3`) as Mongoose and cluster 1 (MPIDR `0x100`-`0x103`) as
Cortex-A53.

## Current state

- The DTSI describes all eight cores, PSCI 0.2 over SMC, GIC-400 at
  `0x11001000` and the 26 MHz generic timer.
- `ArmCpu` supports the GICv2 distributor and boot CPU interface for this
  profile. Secondary-core GICv2 bring-up and XNU hardware boot are not yet
  validated; both are recorded in the device porting record.
- No device has reached a verified checkpoint with this profile yet.

Build through the [UniXNU CLI](https://unixnu.com/building). Read the
[device repository specification](https://unixnu.com/porting/device-repository)
and [device-tree specification](https://unixnu.com/porting/device-tree).
