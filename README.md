# Lorebiter (Lore Arbiter)

> **⚠️ WARNING:** This software is currently under active development.

**Lorebiter** is an AI-powered tabletop roleplaying game (RPG) simulator designed around a **persistent, evolving world state**. Rather than relying on simple stateless chat sessions, Lorebiter treats every location, NPC, historical event, character relationship, and observed fact as a living database entry that persists across sessions and dynamically shapes the narrative.

---

## 🌟 Key Concepts

### 🏛️ Persistent World State
In traditional AI roleplay, long chats suffer from context decay, forgotten facts, and hallucinated continuity. Lorebiter fixes this by maintaining a persistent relational state:
- **Living World Engine**: Every action, NPC interaction, and session summary mutates and evolves the world state.
- **Fact Tracking & Contradiction Resolution**: An internal *Arbiter* evaluates narrative outcomes, tracks observed facts, and prevents narrative inconsistencies without breaking immersion.
- **Long-term Memory & Vector Search**: Past sessions are automatically summarized into persistent lore entries, while vector embeddings (`pgvector`) retrieve distant memories and inject relevant context on-demand.

### 🎭 RPG Simulation & Multi-NPC Orchestration
- **Dynamic Multi-NPC Sessions**: Speak with multiple NPCs concurrently in a single scene. The Game Engine dynamically routes conversational intent and prevents narrator or character hijacking.
- **Inner Thoughts & Insight**: Characters maintain hidden internal reasoning loops that govern their actions, decisions, and emotional states, inspectable via an Insight toggle.
- **World Narrator**: A dedicated narrator handles environmental descriptions, temporal transitions, and scene pacing.

---

## ✨ Features

- **World Management**: Create, export, and import complete self-contained worlds as JSON backups. Paste raw JSON directly for rapid world generation from external AIs.
- **Dynamic Model Selection**: Live integration with [OpenRouter](https://openrouter.ai) allows swapping between hundreds of LLMs per-session.
- **Rich Lore Database**: Define characters, locations, factions, items, and historical events with layered visibility (public, personal, observable).
- **Visual Lore Graph**: Visualize complex webs of character relationships and world connections in an interactive 2D graph.
- **Semantic RAG & Triggers**: Contextually query lore entries using vector embeddings (`pgvector`) and inject pertinent world rules into the prompt.
- **AI Lore Polish & Assistance**: Process unstructured notes or text dumps into cleanly structured lore entries using integrated NLP polish tools.

---

## 🛠️ Tech Stack

- **Framework**: [Next.js](https://nextjs.org/) (App Router)
- **Database & ORM**: PostgreSQL with `pgvector` extension via [Drizzle ORM](https://orm.drizzle.team/)
- **Auth**: Neon Auth (`@neondatabase/auth`)
- **AI Integration**: OpenRouter API & Vector Embeddings
- **UI & Graphing**: React 19, Tailwind CSS v4, Lucide Icons, `react-force-graph-2d`

---

## 🚀 Getting Started

### 1. Prerequisites
- Node.js 20+ installed.
- A PostgreSQL database with `pgvector` support enabled (e.g., local PostgreSQL with `pgvector` or [Neon](https://neon.tech)).
- An [OpenRouter](https://openrouter.ai) API Key.

### 2. Clone and Install
```bash
git clone https://github.com/vxnus-studio/lorebiter.git
cd lorebiter
npm install
```

### 3. Environment Setup
Copy the example environment file:
```bash
cp .env.example .env.local
```
Fill in your configuration details in `.env.local`:
```env
DATABASE_URL="postgres://user:password@localhost:5432/lorebiter"
OPENROUTER_API_KEY="your-openrouter-api-key"
```

### 4. Database Schema Migration
Push the Drizzle schema to your database:
```bash
npx drizzle-kit push
```

### 5. Run Development Server
Start the Next.js development server:
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser to start building your world and playing!

---

## 📄 Deployment

Lorebiter is fully compatible with Vercel and serverless PostgreSQL providers like Neon.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)
