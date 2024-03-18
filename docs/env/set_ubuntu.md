# Create empty image
```bash
qemu-img create -f raw raw 40G
```

# Install Ubuntu Server
```bash
qemu-system-aarch64 \
   -monitor stdio \
   -M virt,highmem=off \
   -accel hvf \
   -cpu host \
   -smp 4 \
   -m 3000 \
   -bios QEMU_EFI.fd \
   -device virtio-gpu-pci \
   -display default,show-cursor=on \
   -device qemu-xhci \
   -device usb-kbd \
   -device usb-tablet \
   -device intel-hda \
   -device hda-duplex \
   -drive file=raw,format=raw,if=virtio,cache=writethrough \
   -cdrom ubuntu-22.04.4-live-server-arm64.iso
```

# Run Ubuntu Server
```bash
alias ubuntu='qemu-system-aarch64 \
   -monitor stdio \
   -M virt,highmem=off \
   -accel hvf \
   -cpu host \
   -smp 4 \
   -m 3000 \
   -bios QEMU_EFI.fd \
   -device virtio-gpu-pci \
   -display default,show-cursor=on \
   -device qemu-xhci \
   -device usb-kbd \
   -device usb-tablet \
   -device intel-hda \
   -device hda-duplex \
   -drive file=raw,format=raw,if=virtio,cache=writethrough'

ubuntu
```
