
# Lab 01 — Investigating CPU Usage on macOS

## Objective

Investigate whether a Mac is experiencing sustained CPU pressure using built-in command-line tools.

## Environment

- Operating system: macOS
- Architecture: ARM64 (Apple Silicon)
- Monitoring tool: `top`
- Test type: Local observation; no system changes made

## Investigation Steps

### 1. Inspect running processes

Command:

```bash
top -o cpu
```

This displays running processes sorted by CPU usage.

### 2. Collect CPU samples

Command:

```bash
top -l 3 -s 2 | grep -E "CPU usage|Load Avg"
```

This collects three samples at two-second intervals and displays CPU utilization and load averages.

## Observed Results

| Metric | Sample 1 | Sample 2 | Sample 3 |
|---|---:|---:|---:|
| User CPU | 3.86% | 1.44% | 3.10% |
| System CPU | 9.16% | 1.44% | 2.16% |
| Idle CPU | 86.96% | 97.11% | 94.81% |

Reported load averages: 1.77, 1.67, and 1.92.

## Analysis

CPU idle time remained high across all three samples. The collected evidence does not indicate sustained CPU saturation during this observation period.

The load averages require additional context, including the number of CPU cores and whether processes are waiting for resources.

No root cause was identified because sustained CPU pressure was not demonstrated.

## Conclusion

The initial investigation did not identify evidence of a CPU saturation problem.

This is a useful troubleshooting outcome: collect evidence, interpret the measurements, and avoid making changes without a demonstrated problem.

## Next Steps

If a user reports system slowness, investigate the reported symptoms and collect additional evidence, such as:

- Memory pressure
- Disk activity
- Application responsiveness
- CPU usage over a longer period

## Skills Practiced

- Command-line monitoring
- Evidence collection
- Metric interpretation
- Technical documentation
- Evidence-based troubleshooting

---

**Disclaimer:** This is a personal learning lab using observations from my own Mac. It is not a production incident or a simulation of a Linux server failure.
