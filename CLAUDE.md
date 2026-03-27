# Packrat - System Information Collector

## Purpose
Collects system information from test endpoints for reproducibility. Gathers hardware, OS, kernel, and configuration details that may affect benchmark results.

## Language
Bash — single script `packrat` (~715 lines)

## Key Files
| File | Purpose |
|------|---------|
| `packrat` | Main collection script — runs on each endpoint during a test |
| `rickshaw.json` | Declares integration with rickshaw (roles, parameters) |
| `workshop.json` | Engine image build requirements (packrat runs on engines/endpoints, not the controller) |

## Collectors
14 parallel collectors: distro, package_manager, env, cpu, device, system, kernel, block, memory, net, cgroup, libvirt, firewall, container

## Conventions
- Primary branch is `master`
- Creates a `packrat-archive/` directory containing collected data, compressed with xz
- Logs activity to `packrat.log`
- Runs as part of the engine script execution phase during a benchmark
- Uses standard Bash modelines and 4-space indentation
