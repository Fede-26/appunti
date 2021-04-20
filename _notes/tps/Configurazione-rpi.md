---
title: Configurazione raspberry pi
toc: true
tags: Tps,Raspberry
Season: winter
---

# Configurazione base rPi

- aprire la partizione `boot`
- aprire il terminale con tasto destro nella cartella
- `sudo touch ssh`
- aprire la partizione `rootfs`
- aprire il terminale con tasto destro nella cartella
- `sudo nano etc/wpa_supplicant/wpa_supplicant.conf`
- aggiungere

```
country=IT

network={
	ssid="NOME RETE"
	psk="PASSWORD RETE"
}
```

- la password della scuola è

```
network={
	ssid="fluff"
	psk="ciccione!"
}
```



- uscire con `ctrl-x` --> `s` / `Y`-->`invio`

- Smontare le partizioni in modo sicuro con il simbolo nella barra laterale del gestore file
- accendere il rPi

# Trovare l'ip

- `ping raspberrypi.local` per vedere se è connesso
- `ssh raspberrypi.local` per connettersi
- sostituire `raspberrypi` con un eventuale hostname settato

- `ip -4 a` per visualizzare l'indirizzo ip del dispositivo

---

## Non ignorare i ping di broadcasts

- entrare nel raspberry
- `sudo nano /etc/rc.local`
- aggiungere questa riga prima di `exit 0`

```bash
echo "0" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
```

- uscire con `ctrl-x` --> `s` / `Y`-->`invio`
- sul pi eseguire `bash /etc/rc.local` per rendere effettive le modifiche senza un riavvio

---

## Ping broadcast

- sul proprio pc
- trovare l'ip di broadcast con `ip -4 a`
![](../../assets/img/rpi-2021-01-20_13-40.png)

- `ping -b indirizzo-di-broadcast`
- digitare `ctrl-c` per terminare il comando