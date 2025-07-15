# alpine-tpm.img for Thalunix

This is a minimal modification of Alpine Linux 3.22, built using `alpine-virt-3.22.0-x86_64.iso`. It is configured to start a TPM 2.0 emulator (`swtpm`) automatically at boot, intended for development and testing with [Thalunix](https://github.com/hejhdiss/Thalunix), a conceptual QEMU manager.

Download:[alpine-tpm-v1](https://github.com/hejhdiss/alpine-tpm/releases/tag/alpine-tpm-v1)

## Usage

Run with QEMU:

```bash
qemu-system-x86_64 -m 512 \
  -drive file=alpine-tpm.img,format=raw \
  -net nic -net user,hostfwd=tcp::2321-:2321,hostfwd=tcp::2322-:2322 \
  -nographic
```

**TPM server will be available on:**

- localhost:2321 (TPM socket)
- localhost:2322 (TPM control)

## Credits and Licensing

This image is fully based on Alpine Linux and includes `swtpm` (a software TPM emulator). All original components retain their respective licenses:

### Alpine Linux

- Source: [https://gitlab.alpinelinux.org/alpine](https://gitlab.alpinelinux.org/alpine)
- Website: [https://alpinelinux.org](https://alpinelinux.org)
- License: Alpine Linux is a collection of packages, primarily licensed under MIT and various FOSS licenses. See:  
  [https://git.alpinelinux.org/aports/plain/LICENSE](https://git.alpinelinux.org/aports/plain/LICENSE)

### swtpm (Software TPM Emulator)

- Project: [https://github.com/stefanberger/swtpm](https://github.com/stefanberger/swtpm)
- License: BSD-3-Clause License  
  [https://github.com/stefanberger/swtpm/blob/master/LICENSE](https://github.com/stefanberger/swtpm/blob/master/LICENSE)

This image only introduces minimal configuration changes (such as running `swtpm` at startup) for development purposes.

Author of modifications and integrator:  
Muhammed Shafin P  
Project: [https://github.com/hejhdiss/Thalunix](https://github.com/hejhdiss/Thalunix)

Please refer to Alpine Linux and swtpm licenses individually before redistribution.



