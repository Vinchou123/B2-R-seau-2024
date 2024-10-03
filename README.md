# B2-Réseau-2024

## TP1 : Maîtrise réseau du votre poste

### I. Basics

☀️ Carte réseau WiFi
Déterminer...

l'adresse MAC de votre carte WiFi
l'adresse IP de votre carte WiFi
le masque de sous-réseau du réseau LAN auquel vous êtes connectés en WiFi en notation CIDR, par exemple /16
```bash
192.168.86.42 /24
```

ET en notation décimale, par exemple 255.255.0.0

```PS C:\Users\vince> ipconfig /all```

``` bash
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   👉 Adresse physique . . . . . . . . . . . : E0-2E-0B-DF-2E-38
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::c621:eec3:93a0:17dd%4(préféré)
   👉 Adresse IPv4. . . . . . . . . . . . . .: 10.33.72.151(préféré)
   👉 Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Bail obtenu. . . . . . . . . . . . . . : jeudi 3 octobre 2024 08:54:59
   Bail expirant. . . . . . . . . . . . . : vendredi 4 octobre 2024 08:54:58
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   IAID DHCPv6 . . . . . . . . . . . : 81800715
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-2D-E0-C4-09-E0-2E-0B-DF-2E-38
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
```
   
☀️ Déso pas déso

Pas besoin d'un terminal là, juste une feuille, ou votre tête, ou un tool qui calcule tout hihi. Déterminer...

l'adresse de réseau du LAN auquel vous êtes connectés en WiFi
```00001010.00100001.01000000.00000000```
l'adresse de broadcast
```10.33.79.255```
le nombre d'adresses IP disponibles dans ce réseau
```4096 adresses IP disponible mais 4094 utilisables car il faut déduire de l'adresse broadcast et l'adresse du réseau ```

☀️ Hostname

déterminer le hostname de votre PC
```bash 
PS C:\Users\vince> hostname
Vincenzo
```

☀️ Passerelle du réseau
Déterminer...

l'adresse IP de la passerelle du réseau
```Passerelle par défaut. . . . . . . . . : 10.33.79.254```
l'adresse MAC de la passerelle du réseau
```bash
PS C:\Users\vince> arp -a

Interface : 10.33.72.151 --- 0x4
  Adresse Internet      Adresse physique      Type
  10.33.69.24           b8-1e-a4-8f-79-47     dynamique
  10.33.73.77           98-8d-46-c4-fa-e5     dynamique
  10.33.77.160          c8-94-02-f8-ab-97     dynamique
  10.33.79.254         👉 7c-5a-1c-d3-d8-76     dynamique
  224.0.0.2             01-00-5e-00-00-02     statique
  224.0.0.22            01-00-5e-00-00-16     statique
  224.0.0.251           01-00-5e-00-00-fb     statique
  224.0.0.252           01-00-5e-00-00-fc     statique
  230.0.0.1             01-00-5e-00-00-01     statique
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
  ```
☀️ Serveur DHCP et DNS
Déterminer...

l'adresse IP du serveur DHCP qui vous a filé une IP
```Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254```
l'adresse IP du serveur DNS que vous utilisez quand vous allez sur internet
```Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8```

☀️ Table de routage
Déterminer...

dans votre table de routage, laquelle est la route par défaut

```PS C:\Users\vince> route print```
```bash
IPv4 Table de routage
===========================================================================
Itinéraires actifs :
Destination réseau    Masque réseau  Adr. passerelle   Adr. interface Métrique
         👉 0.0.0.0          0.0.0.0     10.33.79.254     10.33.72.151     30
         10.4.1.0    255.255.255.0         On-link          10.4.1.2    281
         10.4.1.2  255.255.255.255         On-link          10.4.1.2    281
       10.4.1.255  255.255.255.255         On-link          10.4.1.2    281
       10.33.64.0    255.255.240.0         On-link      10.33.72.151    286
     10.33.72.151  255.255.255.255         On-link      10.33.72.151    286
   
```

### II. Go further

☀️ Hosts ?

faites en sorte que pour votre PC, le nom b2.hello.vous corresponde à l'IP 1.1.1.1

prouvez avec un ping b2.hello.vous que ça ping bien 1.1.1.1
```bash
Statistiques Ping pour 1.1.1.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 15ms, Maximum = 20ms, Moyenne = 17ms
 ```


☀️ Go mater une vidéo youtube et déterminer, pendant qu'elle tourne...

l'adresse IP du serveur auquel vous êtes connectés pour regarder la vidéo
le port du serveur auquel vous êtes connectés
le port que votre PC a ouvert en local pour se connecter au port du serveur distant


Il est fortement recommandé de couper toutes vos autres connexions internet pour identifier facilement ce trafic (fermez Discord, tous les onglets de vos navigateurs ouverts, etc). Fermez tout ce qui sollicite le réseau. 

```
Je l'ai fait avec Wireshark : 
1	0.000000	10.33.72.151	77.136.192.84	UDP	75	65509 → 443 Len=33
2841	68.541727	77.136.192.84	10.33.72.151	UDP	1292	443 → 65509 Len=1250
3002	68.549138	77.136.192.84	10.33.72.151	UDP	1292	443 → 65509 Len=1250

Ip du serveur : 77.136.192.84
Port du serveur : 443
Port local : 65509
```

☀️ Requêtes DNS
Déterminer...

à quelle adresse IP correspond le nom de domaine www.thinkerview.com


Ca s'appelle faire un "lookup DNS".

```
PS C:\Users\vince> nslookup www.thinkerview.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    www.thinkerview.com
Addresses:  👉2a06:98c1:3121::7
          2a06:98c1:3120::7
          👉188.114.96.7
          188.114.97.7
```


à quel nom de domaine correspond l'IP 143.90.88.12

```
PS C:\Users\vince> nslookup 143.90.88.12
Serveur :   dns.google
Address:  8.8.8.8

👉Nom :    EAOcf-140p12.ppp15.odn.ne.jp
Address:  143.90.88.12
```

Ca s'appelle faire un "reverse lookup DNS".

☀️ Hop hop hop
Déterminer...

par combien de machines vos paquets passent quand vous essayez de joindre www.ynov.com

```
PS C:\Users\vince> tracert www.ynov.com

Détermination de l’itinéraire vers www.ynov.com [104.26.11.233]
avec un maximum de 30 sauts :

  1     3 ms     3 ms     1 ms  10.33.79.254
  2     2 ms     2 ms     2 ms  145.117.7.195.rev.sfr.net [195.7.117.145]
  3     3 ms     3 ms     2 ms  237.195.79.86.rev.sfr.net [86.79.195.237]
  4     4 ms     4 ms     4 ms  196.224.65.86.rev.sfr.net [86.65.224.196]
  5    11 ms    12 ms    12 ms  164.147.6.194.rev.sfr.net [194.6.147.164]
  6     *        *       17 ms  162.158.20.24
  7    23 ms    26 ms    16 ms  162.158.20.31
  8    16 ms    16 ms    15 ms  104.26.11.233

Itinéraire déterminé.
PS C:\Users\vince>
```

Les paquets passent par 8 machines pour atteindre www.ynov.com

☀️ IP publique
Déterminer...

l'adresse IP publique de la passerelle du réseau (le routeur d'YNOV donc si vous êtes dans les locaux d'YNOV quand vous faites le TP)

C'est le premier saut soit la première ligne qui correspond à l'adresse IP publique de la passerelle du réseau(routeur d'Ynov).
Donc 10.33.79.254


### III. Le requin

☀️ Capture ARP


📁 fichier arp.pcap

capturez un échange ARP entre votre PC et la passerelle du réseau
vous pouvez vider votre table ARP à l'aide d'une commande, pour forcer l'échange ARP


En bref rappel : pour communiquer avec quelqu'un sur un LAN, il faut connaître son adresse MAC. Vous avez tout le temps besoin de communiquer avec le routeur, car c'est lui qui fait passer vos paquets vers internet. Il est donc nécessaire d'apprendre l'adresse MAC du routeur. Votre PC fait un échange ARP pour apprendre la MAC de quelqu'un sur son LAN, comme le routeur.

[Lien vers capture ARP](arp.pcapng)

☀️ Capture DNS


📁 fichier dns.pcap

capturez une requête DNS vers le domaine de votre choix et la réponse
vous effectuerez la requête DNS en ligne de commande

[Lien vers capture DNS](dns.pcapng)

☀️ Capture TCP


📁 fichier tcp.pcap

effectuez une connexion qui sollicite le protocole TCP
je veux voir dans la capture :

un 3-way handshake
un peu de trafic
la fin de la connexion TCP

[Lien vers capture TCP](TCP.pcapng)


TCP est le protocole qu'on va trouver DANS les paquets IP. Un paquet IP achemine le message jusqu'à une certaine machine, qui peut ouvrir le paquet IP afin de voir un message TCP. Le contenu du message TCP (une requête HTTP par exemple) est alors envoyé à une application (un serveur web par exemple) pour qu'elle traite le contenu.