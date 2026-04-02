1. Conception de la topologie
   - J’ai commencé par créer trois zones dans Packet Tracer : 
-Bureau 1,
-Bureau 2
-Bureau 3
Chacune contenant un switch, un point d’accès Wi‑Fi, un PC portable connecté en Wi‑Fi, deux PC fixes et un téléphone IP.
   - J’ai placé le routeur non loin du switch dans le Bureau 1, et j’ai ajouté un équipement Cloud pour simuler le WAN.

2. Mise en place du câblage
   - J’ai relié chaque équipement filaire (PC fixes, téléphones IP, points d’accès Wi‑Fi) à son switch de bureau.
   - J’ai connecté les trois switches entre eux (Bureau 1 - Bureau 2 - Bureau 3) configurés en trunk.
   - J’ai connecté le routeur au switch du Bureau 1 qui transporte tous les VLAN.

3. Configuration des VLAN sur les switches
   - Sur chaque switch, j’ai créé les VLAN 1 (VOIP), VLAN 10 (WIFI), VLAN 20 (PC_FIXES) et VLAN 30 (ADMIN).
   - J’ai ensuite affecté les ports en fonction du type d’équipement :
     - Ports 2–3 pour les téléphones IP en VLAN 1 (VOIP)
     - Ports 4–5 pour les points d’accès WIFI en VLAN 10
     - Ports 6–7 pour les PC fixes en VLAN 20
     - Port 8 pour le poste d’administration en VLAN 30
   - j’ai configuré les ports 1 et 9 de chaque switch en mode trunk pour transporter l’ensemble des VLAN vers les autres switches et vers le routeur.

4. Configuration du routeur
   - Sur l’interface connectée au switch (G0/1), j’ai créé une sous‑interface par VLAN avec l’encapsulation 802.1Q :
     - une sous‑interface pour le VLAN 1 : 192.168.0.0/24
     - une sous‑interface pour le VLAN 10 : 192.168.10.0/24
     - une sous‑interface pour le VLAN 20 : 192.168.20.0/24
     - une sous‑interface pour le VLAN 30 : 192.168.30.0/24
   - J’ai ensuite configuré un pool DHCP pour chaque VLAN.

5. Configuration des clients
   - Sur les PC fixes, les PC portables et les téléphones IP, j’ai configuré le DHCP.
   - J’ai vérifié que chaque équipement recevait bien une adresse IP dans la plage correspondant à son VLAN.

6. Tests
   - J’ai effectué des pings entre deux machines d’un même VLAN pour vérifier la connexion entre eux.
   - J’ai ensuite testé des pings entre des machines de VLAN différents (un PC fixe du bureau 1 / VLAN 20 vers le Bureau 3 / VLAN 10 PC Portable) pour vérifier le routage inter‑VLAN via le routeur.
  
   - Vous trouverez toutes les captures d'écrans ainsi que toutes les config du switch et du routeur dans les piéces jointes.

