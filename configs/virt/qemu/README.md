# Virtualization: Qemu

This package enables compiling & running a qemu virtual machine.

**NOTE: GCC 8 or newer is required for host-qemu to be compiled.**

Builds both the host qemu VM and the target OS.

```sh
$ SKIFF_CONFIG=intel/x64,virt/qemu make configure compile
$ make cmd/virt/qemu/run
```

You can press ctrl+a and then c (followed by return) to switch between the
serial output and the qemu monitor. The "stop" command in the monitor shell will
stop emulation, or you can use `killall qemu-system`.

Log in as "root" for the default Skiff setup.

The `intel/x64` portion of `SKIFF_CONFIG` can be replaced with any of the
SkiffOS targets, including the arm and riscv64 systems.

## Using UTM on MacOS

For compiling on MacOS, see [Compile on MacOS].

[Compile on MacOS]: https://github.com/skiffos/SkiffOS?tab=readme-ov-file#compile-on-macos

```bash
export SKIFF_CONFIG=apple/arm,skiff/core,virt/qemu
make configure compile
make cmd/virt/utm/buildutm
```

Copy `workspaces/default/images/skiffos.utm` to your Mac, on Lima:

```
cp workspaces/default/images/skiffos.utm /opt/skiffos-build
```

[Install UTM](https://getutm.app) on your MacOS machine.

Run `open ~/skiffos-build` and double-click the skiffos.utm file to start the VM!
