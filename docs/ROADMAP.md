# Roadmap

These are planning estimates, not commitments. They assume one developer working part time.

| Milestone | Goal | Target (likely) | State |
| --- | --- | --- | --- |
| M0 | Native feasibility: handshake, tracking, video in headset | 2026-09-26 | Done on one Quest 3 |
| M1 | Stable session, reconnect and sleep recovery | 2026-10 | In progress |
| M2 | Complete controller and hand input | 2026-10 | Partial |
| M3 | Full-resolution GPU rendering and encoding in the headset | 2026-11 | Partial (offline) |
| M4 | Long-running host service | 2026-12 | Groundwork |
| M5 | OpenXR runtime alpha (standard VR apps) | 2027-02 | Planned |
| M6 | Headset audio and haptics | 2027-03 | Planned |
| M7 | Launching games, returning to home | 2027-04 | Planned |
| M8 | Performance benchmark on documented hardware | 2027-05 | Planned |
| M9 | Packaging and public beta | ~2027-06 | Planned |

In parallel, the world and editor track continues: worlds, avatars, tools and later shared spaces.

```mermaid
gantt
    title qlink roadmap (likely case)
    dateFormat YYYY-MM-DD
    axisFormat %Y-%m
    section Runtime
    M1 Stable session        :m1, 2026-09-28, 3w
    M3 GPU render + encode   :m3, after m1, 5w
    M4 Host service          :m4, 2026-11-09, 4w
    M5 OpenXR alpha          :m5, after m4, 10w
    M6 Audio and haptics     :m6, 2027-02-15, 6w
    M7 Game compatibility    :m7, after m5, 6w
    M8 Benchmark             :m8, after m7, 4w
    M9 Public beta           :m9, after m8, 6w
```
