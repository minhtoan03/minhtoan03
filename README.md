- 👋 Hi, I’m @minhtoan03
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
minhtoan03/minhtoan03 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
wget -O b64.bin "https://github.com/BlankOn/ovmf-blobs/raw/master/bios64.bin"
wget -O w10.iso "https://software.download.prss.microsoft.com/dbazure/Win10_22H2_English_x64v1.iso?t=dea19548-4272-448f-9cb8-54449bc2239e&e=1691544476&h=007e7f448c46823b392e6f2b3fd8dda977ba8271be8642e88632731062764a13"
wget -O ngrok.tgz "https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz"
tar -xf ngrok.tgz
rm -rf ngrok.tgz
./ngrok config add-authtoken 2TgIMoL7ES14OfDHwRKCUk9uQKC_7wNyijoBgYc39fH5sLzdV
./ngrok tcp 5900
sudo apt-get update
sudo apt-get install qemu-kvm -y
qemu-img create -f raw w11.img 64G
sudo qemu-system-x86_64 -m 4G -cpu host -boot order=c -drive file=w10.iso,media=cdrom -drive file=w11.img,format=raw -device usb-ehci,id=usb,bus=pci.0,addr=0x4 -device usb-tablet -vnc :0 -smp cores=2 -device rtl8139,netdev=n0 -netdev user,id=n0 -vga qxl -accel kvm -bios b64.bin

