# Yobbul — Project Tracker

App de livraison pour l'Afrique de l'Ouest. Ce dépôt centralise le suivi de toutes les features via GitHub Issues + Project Board.

## Architecture

| Projet | Stack | Port |
|---|---|---|
| `yobbul-api` | NestJS monorepo (7 microservices) | 3001–3008 |
| `yobbul-client` | React Native / Expo (app client) | — |
| `yobbul-pro` | React Native / Expo (app livreur) | — |
| `yobbul-admin` | Vite + React + shadcn/ui | 5173 |
| `yobbul-ai` | FastAPI + LightGBM + Claude | 8000 |

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

## Services — ports

| Service | Port |
|---|---|
| auth | 3001 |
| orders | 3002 |
| tracking (WS) | 3003 |
| payments | 3004 |
| notifications | 3005 |
| drivers | 3006 |
| chat | 3008 |
| yobbul-ai (FastAPI) | 8000 |
| yobbul-admin (Vite) | 5173 |
| MailHog UI | 8025 |
