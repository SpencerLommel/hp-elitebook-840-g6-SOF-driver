# HP EliteBook 840 G6 - SOF Driver Issue
This repository contains diagnostic data, logs, and analysis for the Sound Open Firmware (SOF)
audio driver failure on HP EliteBook 840 G6 (Intel Cannon Point-LP High Definition Audio Controller).

## Problem
The SOF DSP fails to boot on Ubuntu 25.04 (kernel 6.8+), resulting in no audio output
("Dummy Output"). Logs show:
`error: dsp init failed after 3 attempts with err: -110`


## Goal
The goal of this repo is to track progress and provide one place with all the logs and diagnostic data for this issue.
Once I solve this issue I plan on forming a patch and upstreaming this to SOF or whatever kernel subsystem is related to this issue.
