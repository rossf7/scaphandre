All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased](https://github.com/hubblo-org/scaphandre/commits/dev)

Please check dev branch.

## [1.0.1](https://github.com/hubblo-org/scaphandre/releases/tag/v1.0.1)

### Added

- Added installation instructions for Debian and Ubuntu, see [#379](https://github.com/hubblo-org/scaphandre/pull/379), thanks @LarsSven

### Changed

- Qemu has been added back to the default list of features, see [#381](https://github.com/hubblo-org/scaphandre/pull/381), thanks @LarsSven

### Fixed

- Improved documentation on [RAPL Domains and metric]s(https://hubblo-org.github.io/scaphandre-documentation/explanations/rapl-domains.html), see [#116](https://github.com/hubblo-org/scaphandre/issues/116), [#177](https://github.com/hubblo-org/scaphandre/issues/177), [#241](https://github.com/hubblo-org/scaphandre/issues/241)
- Fixed faulty output from JSON exporter, see [#369](https://github.com/hubblo-org/scaphandre/issues/369)
- Fixed truncated JSON output dur to buffer size, see [#359](https://github.com/hubblo-org/scaphandre/issues/359)

## [1.0.0](https://github.com/hubblo-org/scaphandre/releases/tag/v1.0.0)

### Added

- Host resources consumption metrics : scaph_host_swap_total_bytes, scaph_host_swap_free_bytes, scaph_host_memory_free_bytes, scaph_host_memory_available_bytes, scaph_host_memory_total_bytes, scaph_host_disk_total_bytes, scaph_host_disk_available_bytes, scaph_host_cpu_frequency, scaph_host_load_avg_fifteen, scaph_host_load_avg_five, scaph_host_load_avg_one - see https://hubblo-org.github.io/scaphandre-documentation/references/metrics.html for details, https://github.com/hubblo-org/scaphandre/issues/271 and https://github.com/hubblo-org/scaphandre/pull/278 for reference
- Per-process resource consumption metrics : scaph_process_cpu_usage_percentage, scaph_process_memory_bytes, scaph_process_memory_virtual_bytes, scaph_process_disk_total_write_bytes, scaph_process_disk_write_bytes, scaph_process_disk_read_bytes, scaph_process_disk_total_read_bytes - see https://hubblo-org.github.io/scaphandre-documentation/references/metrics.html for details, https://github.com/hubblo-org/scaphandre/issues/141 and https://github.com/hubblo-org/scaphandre/pull/274 for reference
- Added service monitor to helm chart, see https://github.com/hubblo-org/scaphandre/pull/230, thanks @mmadoo
- Added packaging folder with sample systemd services files, see https://github.com/hubblo-org/scaphandre/pull/317 and https://github.com/hubblo-org/scaphandre/issues/261, thanks @jcaesar
- Added prometheus push mode exporter, see https://github.com/hubblo-org/scaphandre/issues/269
- Added RPM build github action workflow, see https://github.com/hubblo-org/scaphandre/issues/310
- Added RAPL mmio metric, when the domain is present, see https://github.com/hubblo-org/scaphandre/issues/318 and https://github.com/hubblo-org/scaphandre/pull/329
- Added specific RAPL PSYS metric, when available, see https://github.com/hubblo-org/scaphandre/issues/316 and https://github.com/hubblo-org/scaphandre/pull/329
- Filtering per process in JSON exporter, see https://github.com/hubblo-org/scaphandre/issues/216
- Github action workflow to build Windows EXE installer on each release, see https://github.com/hubblo-org/scaphandre/pull/333
- Github action workflow to build DEB package on each release, see https://github.com/hubblo-org/scaphandre/pull/352, thanks @bdromard
- Added warning messages when powercap files permissions won't allow Scaphandre to read RAPL data, see https://github.com/hubblo-org/scaphandre/issues/214

### Changed

- Global power metrics have changed and could give higher numbers than previously. Please have a look at the [documentation](https://hubblo-org.github.io/scaphandre-documentation/explanations/host_metrics.html).
- `scaph_self_mem_total_program_size`, `scaph_self_mem_resident_set_size` and `scaph_self_mem_shared_resident_size` are replaced by `scaph_self_memory_bytes` and `scaph_self_memory_virtual_bytes`, see https://github.com/hubblo-org/scaphandre/pull/274/files
- Refactored warp10 exporter, see https://github.com/hubblo-org/scaphandre/pull/291 and https://github.com/hubblo-org/scaphandre/issues/105
- Refactored exporters creation with clap4, see https://github.com/hubblo-org/scaphandre/pull/292, thanks @TheElectronWill
- Default docker-compose sets a privileged container now, otherwise it doesn't work in an apparmor context, see https://github.com/hubblo-org/scaphandre/issues/135 and https://github.com/hubblo-org/scaphandre/commit/a1a06ea280b8e66067b2c3b73ac08a377604eb61
- Moved from procfs, to sysinfo, see https://github.com/hubblo-org/scaphandre/issues/267

### Fixed

- Fixed doc broken links, see https://github.com/hubblo-org/scaphandre/pull/259 and https://github.com/hubblo-org/scaphandre/issues/288, thanks @homersimpsons
- Now works on more than 1 vcpu Qemu/KVM virtual machines, see https://github.com/hubblo-org/scaphandre/issues/133 and https://github.com/hubblo-org/scaphandre/pull/207, thanks @tawalaya
- Fix for Kubernetes, don't create PSP if version of kubernetes is above 1.25, see https://github.com/hubblo-org/scaphandre/pull/250, thanks @rossf7
- Fixed bug in --containers flag, see https://github.com/hubblo-org/scaphandre/pull/326, thanks rossf7
- Fix on qemu exporter, see https://github.com/hubblo-org/scaphandre/issues/260
- Fixed panics on regex filters, see https://github.com/hubblo-org/scaphandre/issues/295
- Fixed invalid escape sequence in Prometheus exporter, see https://github.com/hubblo-org/scaphandre/issues/204, thanks @demeringo
- Removed broken python bindings, until it is fixed, see https://github.com/hubblo-org/scaphandre/pull/315 and https://github.com/hubblo-org/scaphandre/issues/296

## [0.5.0](https://github.com/hubblo-org/scaphandre/releases/tag/v0.5.0)

### Changed

- Upgraded procfs to 0.12 : [#144](https://github.com/hubblo-org/scaphandre/pull/144)
- Rollbacked to ubuntu 20.04 as the base docker image : [#151](https://github.com/hubblo-org/scaphandre/pull/151), thanks to @demeringo
- Using github action to tag docker image : [#160](https://github.com/hubblo-org/scaphandre/pull/160), thanks to @rossf7

### Added

- New level of abstraction regarding structs managed by Sensors, so we could implement more sensors in an easier way : [#149](https://github.com/hubblo-org/scaphandre/pull/149)
- Enable JSON exporter to run as a daemon : [#169](https://github.com/hubblo-org/scaphandre/issues/169)
- First building blocks for conditional compilation depending on the OS : [#148](https://github.com/hubblo-org/scaphandre/pull/148)
- Mitigation for machines where powercap is not able to feed rapl domain folders, and only has socket ones : [#198](https://github.com/hubblo-org/scaphandre/pull/198)
- Experimental support for Windows 10, 11, server 2019 : [#74](https://github.com/hubblo-org/scaphandre/issues/74) and [#247](https://github.com/hubblo-org/scaphandre/issues/247)
- Added --containers option to JSON exporter : [#217](https://github.com/hubblo-org/scaphandre/issues/217)

### Fixed

- Kubernetes pods using containerd are now supported : [#130](https://github.com/hubblo-org/scaphandre/pull/130), thanks to @rossf7
- Excluded unrelevant procfs metrics from calculation of cpu cycles consumed by processes : [#132](https://github.com/hubblo-org/scaphandre/pull/132)
- Mitigated possible decrepancies between host (rapl) total power usage metric and the sum of per-process power usage metrics : [#20](https://github.com/hubblo-org/scaphandre/issues/20), note that some issues show remaining issues on this topic. Further investigation and work needed.
- Documentation fix for helm install : [#136](https://github.com/hubblo-org/scaphandre/pull/136), thanks to @arthurzenika
- New helm chart values: arguments and backtrace : [#139](https://github.com/hubblo-org/scaphandre/pull/139), thanks to @jotak
- Some documentation typos : [#157](https://github.com/hubblo-org/scaphandre/pull/157), thanks to @metacosm
- Aligning on new clippy rules : [#162](https://github.com/hubblo-org/scaphandre/pull/162), thanks to @demeringo
- Always set last pods check timestamp : [#173](https://github.com/hubblo-org/scaphandre/pull/173), thanks to @rossf7
- Support kubelets using systemd cgroup driver: [#146](https://github.com/hubblo-org/scaphandre/pull/146), thanks to @rossf7
- Fix missing volume in psp (helm chart): [#168](https://github.com/hubblo-org/scaphandre/pull/168), thanks to @olevitt
- Spelling check in documentation : [#183](https://github.com/hubblo-org/scaphandre/pull/183), thanks to @irishgordo
- No more duplicated HELP and TYPE lines in prometheus exporter: [#165](https://github.com/hubblo-org/scaphandre/issues/165) and [#192](https://github.com/hubblo-org/scaphandre/pull/192)
- Escaping newlines in cmdline: [#175](https://github.com/hubblo-org/scaphandre/issues/175), thanks to @uggla

## [0.4.1](https://github.com/hubblo-org/scaphandre/releases/tag/v0.4.0)

### Changed

- Updated k8s-sync crate to 0.2.3 to get authentication by token feature

## [0.4.0](https://github.com/hubblo-org/scaphandre/releases/tag/v0.4.0)

### Added

- Riemann exporter now supports mTLS: [#103](https://github.com/hubblo-org/scaphandre/pull/103) thanks @uggla !
- `--containers` option, in prometheus exporter, tells scaphandre to add labels to metrics related to a docker container or a kubernetes pod, to make getting metrics of a distributed application easier: [#84](https://github.com/hubblo-org/scaphandre/pull/109) thanks @rossf7 for the tests, feedbacks, helm configuration and thanks @uggla for the reviews !
- stdout exporter now allows to choose the number of processes to watch, with the --process-number flag and to filter processes watched thanks to a regex, with the --regex-filter option: [#98](https://github.com/hubblo-org/scaphandre/pull/98), thanks @uggla !
- MetricGenerator includes timestamp in Metrics now : [#113](https://github.com/hubblo-org/scaphandre/pull/113)

### Fixed

- Added Cargo.lock to the repository: [#111](https://github.com/hubblo-org/scaphandre/issues/111)
- Ensured domains names are feteched properly in any case : [#114](https://github.com/hubblo-org/scaphandre/pull/114) thanks @PierreRust !

### Changed

- Manipulating flags as a Vec of clap::Arg instead of a HashMap of ExporterOption in exporters: [#100](https://github.com/hubblo-org/scaphandre/pull/100), thanks @uggla !
- Json and Stdout exporters are now using MetricGenerator as an inteface to get metrics properly : [#113](https://github.com/hubblo-org/scaphandre/pull/113)

## [0.3.0](https://github.com/hubblo-org/scaphandre/releases/tag/v0.3.0)

### Added

- New MetricGenerator and Metric structs and helper functions to make writing exporters easier. Riemann and Prometheus exporters now share the same code pattern: [#79](https://github.com/hubblo-org/scaphandre/pull/79) thanks @uggla !
- New [Warp10](https://warp10.io/) exporter ! [#76](https://github.com/hubblo-org/scaphandre/pull/76)
- Updated riemann_client and protobuf crates dependencies [#70](https://github.com/hubblo-org/scaphandre/pull/70/files) thanks @uggla !
- Successfully tested on AMD CPUs (AMD Ryzen 5 2600X): [#55](https://github.com/hubblo-org/scaphandre/issues/55) (requires a kernel 5.11 or later) thanks @barnumbirr and @kamaradclimber !
- Scaphandre can now be tested locally thanks to a docker-compose stack ! [#61](https://github.com/hubblo-org/scaphandre/pull/61) thanks @PierreRust !
- Added a CITATION file for references: [#95](https://github.com/hubblo-org/scaphandre/issues/95) thanks @tstrempel !

### Fixed

- Allowing scaphandre to run even if intel_rapl modules are not found: [#65](https://github.com/hubblo-org/scaphandre/pull/65) (needed to run scaphandre on AMD CPUs)
- Fixed typos and lacks in the documentation: [#81](https://github.com/hubblo-org/scaphandre/pull/81), [#77](https://github.com/hubblo-org/scaphandre/pull/77), [#80](https://github.com/hubblo-org/scaphandre/issues/80) thanks @pierreozoux, @LudovicRousseau, @maethor, @wallet77
- Moved documentation output to another [repository](https://github.com/hubblo-org/scaphandre-documentation): [#94](https://github.com/hubblo-org/scaphandre/pull/94) (documentation is now available here: [https://hubblo-org.github.io/scaphandre-documentation](https://hubblo-org.github.io/scaphandre-documentation))
- Json exporter has been refactored: [#87](https://github.com/hubblo-org/scaphandre/pull/87) thanks @jdrouet !

## [0.2.0](https://github.com/hubblo-org/scaphandre/releases/tag/v0.2.0)

### Added

- Docker image ([hubblo/scaphandre](https://hub.docker.com/r/hubblo/scaphandre)), ubuntu based: [#48](https://github.com/hubblo-org/scaphandre/pull/48), thanks @rossf7
- Helm chart to run scaphandre as a DaemonSet in a kubernetes cluster: [#72](https://github.com/hubblo-org/scaphandre/pull/72) - thanks @rossf7
- JsonExporter, to get metrics in JSON either in stdout or files: [#68](https://github.com/hubblo-org/scaphandre/pull/68) - thanks @wallet77
- RiemannExporter, to send metrics to [Riemann](http://riemann.io) monitoring tool: [#58](https://github.com/hubblo-org/scaphandre/pull/58) - thanks @uggla
- --qemu flag on PrometheusExporter, to add a "vmname" label to metrics related to processes that represent qemu-kvm virtual machines: [#41](https://github.com/hubblo-org/scaphandre/pull/41) - thanks @uggla
- Better documentation structure (based on [divio's documentation framework](https://documentation.divio.com/) and [mdbook](https://rust-lang.github.io/mdBook/)): [#45](https://github.com/hubblo-org/scaphandre/pull/45), result here:  [https://hubblo-org.github.io/scaphandre-documentation/](https://hubblo-org.github.io/scaphandre/)
- Automated CI tests including cargo test --all, running on a (bare metal) machine: [#62](https://github.com/hubblo-org/scaphandre/pull/62)

### Fixed

- Improved QemuExporter documentation: [#42](https://github.com/hubblo-org/scaphandre/pull/42) - thanks @uggla

## [0.1.1](https://github.com/hubblo-org/scaphandre/releases/tag/v0.1.1)

### Added

- `-s, --step` option added by @Uggla, to specify time step between two measurements, when using StdoutExporter

### Removed

- removed `energy_records_to_power_record` function `from src/sensors/mod.rs`. `get_records_diff_power_microwatts` functions from Topology and CPUSocket should be used instead

### Fixed

- README typos and misusage of english fixed by @Uggla and @florimondmanca
- @Uggla made init.sh script more robust
- cleaning of internal structs (records, cpustat, processes) was buggy, it is fixed
- linux kernels < 5, on intel CPUs (>2012) may me measurable now (fixed kernel modules names check)


## [0.1.0](https://github.com/hubblo-org/scaphandre/releases/tag/v0.1.0)

### Added

- Exporters and sensors design.
- Stdout exporter.
- Prometheus exporter.
- Powercap_rapl sensor.
- Qemu exporter.

## HELP

Here are the sub-sections that can be included in each release section:

- **Added** for new features.
- **Changed** for changes in existing functionality.
- **Deprecated** for soon-to-be removed features.
- **Removed** for now removed features.
- **Fixed** for any bug fixes.
- **Security** in case of vulnerabilities.
