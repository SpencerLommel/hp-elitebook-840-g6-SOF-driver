### Hardware
- Model: HP EliteBook 840 G6
- Audio: Intel Cannon Point-LP High Definition Audio Controller (8086:9dc8)
- BIOS: R70 Ver. 01.31.00

### Software
- Ubuntu 25.04 (kernel 6.14.0-33-generic)
- ALSA 1.2.13, PipeWire running
- SOF firmware: `intel/sof/sof-cnl.ri`  
  Topology: `intel/sof-tplg/sof-hda-generic-4ch.tplg`

### Problem

Audio shows “Dummy Output” only.  
SOF driver loads but DSP fails to boot.

### Key issue lines
```
[   14.765244] snd_hda_intel 0000:00:1f.3: Digital mics found on Skylake+ platform, using SOF driver
[   16.960734] sof-audio-pci-intel-cnl 0000:00:1f.3: error: dsp init failed after 3 attempts with err: -110
[   16.960756] sof-audio-pci-intel-cnl 0000:00:1f.3: Failed to start DSP
[   16.960761] sof-audio-pci-intel-cnl 0000:00:1f.3: error: failed to boot DSP firmware -110
```

### Workaround
Adding `options snd-intel-dspcfg dsp_driver=1` to `/etc/modprobe.d/alsa-base.conf` allows audio to work with the legacy HDA driver instead of SOF. 

### Logs & other info

All info above is taken from files within `logs` & `info`. Reference there if you need some more info not included here.