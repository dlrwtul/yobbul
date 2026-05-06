# Yobbul — Project Tracker

App de livraison pour l'Afrique de l'Ouest. Ce dépôt centralise le suivi de toutes les features via GitHub Issues + Project Board.

## Architecture

| Projet | Stack | Accès |
|---|---|---|
| `yobbul-api` | NestJS — 1 gateway + 7 microservices | gateway :3000, WS :3003 |
| `yobbul-client` | React Native / Expo (app client) | — |
| `yobbul-pro` | React Native / Expo (app livreur) | — |
| `yobbul-admin` | Vite + React + shadcn/ui | :5173 |
| `yobbul-ai` | FastAPI + LightGBM + Claude | :3007 |

```
yobbul-client  ─┐
yobbul-pro     ─┤──► gateway:3000 ──► microservices (réseau Docker interne)
yobbul-admin   ─┘
                       WebSocket tracking → :3003 (connexion directe)
```

## Ports exposés à l'hôte (dev)

| Port | Service |
|---|---|
| **3000** | gateway REST — point d'entrée unique |
| **3003** | tracking WebSocket |
| **3007** | yobbul-ai FastAPI |
| 5173 | yobbul-admin Vite |
| 5432 / 6379 / 9092 / 27017 / 8025 | Infrastructure (Postgres, Redis, Kafka, MongoDB, MailHog) |

## Suivi des features

Voir le **[Project Board](https://github.com/dlrwtul/yobbul/projects)** pour l'état de chaque feature.

### Workflow inter-sessions
Au début de chaque nouvelle session Claude Code :
1. Ouvre le Project Board
2. Identifie les issues "In Progress" ou "Todo" prioritaires
3. Dis à Claude Code :
   > *"On travaille sur Yobbul. Le tracker est sur https://github.com/dlrwtul/yobbul. Aujourd'hui on implémente l'issue #[N] : [titre]. Les docs sont dans docs/."*

### Labels utilisés
| Label | Signification |
|---|---|
| `sprint-1` … `sprint-7` | Sprint d'appartenance |
| `api` `client` `pro` `admin` `ai` | Sous-projet ciblé |
| `bug` | Régression ou comportement incorrect |
| `blocked` | En attente d'une dépendance externe |
| `verified` | Testé et validé en local |

