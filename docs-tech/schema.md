
# 📘 WahkoLab Database Schema

This document outlines the entity-relationship model for the WahkoLab platform.

---

## 🧑 `users`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `wallet_address` | TEXT | Ethereum or compatible address |
| `github_username` | TEXT | Linked GitHub username |
| `discord_id` | TEXT | Discord user ID |
| `username` | TEXT | Display name |
| `joined_at` | TIMESTAMP | Date joined |

---

## 🎮 `projects`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `name` | TEXT | Project title |
| `slug` | TEXT | URL-friendly identifier |
| `description` | TEXT | Overview |
| `status` | TEXT | e.g., draft, active, archived |
| `token_address` | TEXT | Smart contract address |
| `created_at` | TIMESTAMP | Creation date |

---

## 🪙 `tokens`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `project_id` | UUID | **FK → projects.id** |
| `user_id` | UUID | **FK → users.id** |
| `amount` | NUMERIC | Number of tokens granted |
| `source` | TEXT | "task", "airdrop", etc. |
| `tx_hash` | TEXT | Blockchain transaction hash |
| `timestamp` | TIMESTAMP | Issued time |

---

## 📋 `tasks`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `project_id` | UUID | **FK → projects.id** |
| `title` | TEXT | Task summary |
| `description` | TEXT | Full task spec |
| `status` | TEXT | proposed, active, done, etc. |
| `created_by` | UUID | **FK → users.id** |
| `claimed_by` | UUID | **FK → users.id** |
| `validated_by` | UUID[] | **FK → users.id** |
| `token_value` | NUMERIC | Token reward |
| `complexity` | TEXT | small, medium, large |
| `created_at` | TIMESTAMP | Task creation time |

---

## 🗳️ `proposals`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `project_id` | UUID | **FK → projects.id** |
| `title` | TEXT | Proposal name |
| `description` | TEXT | Details and rationale |
| `created_by` | UUID | **FK → users.id** |
| `status` | TEXT | open, passed, failed |
| `quorum_required` | NUMERIC | % needed to validate |
| `created_at` | TIMESTAMP | Created on |
| `voting_deadline` | TIMESTAMP | Deadline for votes |

---

## ✅ `votes`
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `proposal_id` | UUID | **FK → proposals.id** |
| `user_id` | UUID | **FK → users.id** |
| `vote_value` | TEXT | yes, no, abstain |
| `weight` | NUMERIC | Token-based vote weight |
| `timestamp` | TIMESTAMP | Voted at |

---

## 🌐 `webhooks_github` (optional)
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `event_type` | TEXT | push, PR, etc. |
| `payload` | JSON | GitHub event body |
| `received_at` | TIMESTAMP | Event time |

---

## 💬 `discord_logs` (optional)
| Field | Type | Description |
|-------|------|-------------|
| `id` | UUID | **Primary key** |
| `user_id` | UUID | **FK → users.id** |
| `channel_id` | TEXT | Channel where message posted |
| `message` | TEXT | Content of message |
| `timestamp` | TIMESTAMP | Sent time |
