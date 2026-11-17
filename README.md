# MOPIC

**Glasses-free 3D displays, and the software that drives them.**

MOPIC builds autostereoscopic (glasses-free) 3D displays and the software behind them: 3D optics, eye tracking and real-time image processing. The company was spun off from Samsung Electronics' C-Lab in 2015 and is based in Anyang, South Korea.

[mopiclabs.com](https://www.mopiclabs.com/en/)

## What we do here

Our displays show a stereo pair to a viewer without a headset, so we run PC games and apps through OpenXR. This account holds the open parts of that work.

| Repository | What it is |
| --- | --- |
| [UEVR](https://github.com/mopiclabs/UEVR) | Our fork of UEVR for glasses-free 3D displays. Branch `mopic/joeyhodge-base` follows the [joeyhodge/UEVR](https://github.com/joeyhodge/UEVR) release line, with our patches listed in [`MOPIC.md`](https://github.com/mopiclabs/UEVR/blob/mopic/joeyhodge-base/MOPIC.md). |
| [uevr-frontend](https://github.com/mopiclabs/uevr-frontend) | The injector we build with it, forked from joeyhodge/uevr-frontend. |

## Why a glasses-free display needs its own patches

A headset has a fixed field of view and two screens. Our display has one panel and tracks the viewer's eyes, so a few things differ:

- The field of view changes every frame as the viewer moves, and the frustum is off-axis.
- Both eyes are seen side by side on the same panel, so a difference in brightness or shading between them is easy to notice.
- Games start, change resolution and quit on a desktop monitor, not inside a headset session.

Most of our UEVR patches come from those three points. Many of them are general fixes (startup and exit hangs, per-eye rendering differences, OpenXR correctness), and we plan to send those upstream as small pull requests.

## How we work

- UEVR is the work of [praydog](https://github.com/praydog/UEVR), and we build on [joeyhodge](https://github.com/joeyhodge/UEVR)'s continued development. Thank you both.
- We test on real games with an automated harness, on our own OpenXR runtime (based on [Monado](https://monado.freedesktop.org/)). When we have not tested something on a headset runtime, we say so.
- Much of our code is written with AI assistance (Claude) and reviewed and tested by us. Commits carry a `Co-Authored-By` line when that is the case.
