## What this adds

`Sinux Installer 1.1.0` — a terminal-only live installer ISO for the Sinux
kernel (a from-scratch OS, not Linux). The ISO is a minimal Linux vehicle;
what gets written to the target disk is the Sinux Multiboot2 kernel.

* BIOS + UEFI (El Torito / EFI system partition image), Secure Boot off
* English + Farsi/Persian catalogs (including a pre-shaped VGA console catalog)
* GPT layout with BIOS Boot Partition + ESP + root (ext2/ext4), 4Kn-safe
* PID 1 supervisor in `/init` (fixes `Attempted to kill init`)
* Console hotfix: default entries use `console=tty0` only; the old
  `console=tty0 console=ttyS0,115200` bound `/dev/console` to a COM port
  that does not exist on most PCs, producing a blank screen with one blinking
  cursor
* Post-install handover: interactive install reboots automatically, ISO GRUB
  detects the installed system and boots it even with the USB stick attached,
  and UEFI gets a real NVRAM `BootNext` entry
* `tests/qemu-tests.sh`: T1–T16, 74 passed / 0 failed / 0 kernel panics

## Verification

`verification-1.1.0.log` and `evidence/*.png` (raw QEMU QMP framebuffer dumps)
are included. SHA256 of the released ISO:
`aa416b0e2569d4275f1778c8dac05bb3df04bc2be4725e2f2ae9837d5eb78535`

## Note

The ISO itself is not committed (66 MB). Publish it as a GitHub Release asset.

Signed-off-by: AM <Araz0-0dev@users.noreply.github.com>
