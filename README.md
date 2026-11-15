From d2c6f4971812941cb1fba2f8a5b3b218f2e85999 Mon Sep 17 00:00:00 2001
From: Claude <noreply@anthropic.com>
Date: Sun, 15 Nov 2026 04:58:53 +0000
Subject: [PATCH] README: remove external project references and starter/sample
 wording

Co-Authored-By: Claude Haiku 5.5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01HQtiUHqZJAVdhPLpdTmyhA
---
 README.md | 23 ++++++++---------------
 1 file changed, 8 insertions(+), 15 deletions(-)

diff --git a/README.md b/README.md
index ee11e05..29381aa 100644
--- a/README.md
+++ b/README.md
@@ -1,19 +1,17 @@
-# LangGraph Incident Triage: Starter Repo
+# LangGraph Incident Triage
 
-Starting code for the NextWork Project **Build a Multi-Agent Incident Triage System with LangGraph**.
+Multi-agent incident triage with LangGraph: a router, specialist agents that investigate in parallel, recovery when one of them crashes, and an approval gate for each team that owns a fix.
 
-`app.py` is the finished single-analyst incident workflow from the NextWork Project [Build a Resumable LangGraph Workflow](https://nextwork.ai/projects/f94db9b2-1157-404b-a559-83e8752f2f86). It is included unchanged. One Gemini call analyzes an incident, a deterministic policy decides whether a human must approve, `interrupt()` pauses the run, and `SqliteSaver` lets a new process resume it. You don't need to have done that Project first: this repo gives you the same starting point either way.
-
-In this Project you turn that single analyst into a team: a router, specialist agents that investigate in parallel, recovery when one of them crashes, and an approval gate for each team that owns a fix. The setup code for the specialists and the status page is already here, so you spend your time on the agents and the graph.
+`app.py` is a single-analyst incident workflow. One Gemini call analyzes an incident, a deterministic policy decides whether a human must approve, `interrupt()` pauses the run, and `SqliteSaver` lets a new process resume it. The setup code for the specialists and the status page is already in this repo, so the work is in the agents and the graph.
 
 ## What's in the repo
 
 | Path | What it is |
 |---|---|
-| `app.py` | The starting workflow: `start` and `resume` commands, one analyst, one approval gate |
-| `specialists.py` | Setup code for the specialist agents: the Gemini model connection, a fixture loader, and one tool each for logs, deploys, and metrics. You add the agents themselves in the Project |
-| `status_page.py` | The web page for the Secret Mission: HTML, styling, and a small server for Cloud Shell Web Preview. You write the part that reads an incident's saved state |
-| `requirements.txt` | Pinned packages. `langchain` is new in this Project (for `create_agent`) |
+| `app.py` | The workflow: `start` and `resume` commands, one analyst, one approval gate |
+| `specialists.py` | Setup code for the specialist agents: the Gemini model connection, a fixture loader, and one tool each for logs, deploys, and metrics. The agents themselves are not written yet |
+| `status_page.py` | The web page for viewing incident runs: HTML, styling, and a small server for Cloud Shell Web Preview. The part that reads an incident's saved state is not written yet |
+| `requirements.txt` | Pinned packages. `langchain` provides `create_agent` |
 | `data/alerts.json` | Two alerts to triage: `INC-2041` (checkout errors) and `INC-2042` (search latency) |
 | `data/logs.jsonl` | Application logs from the services involved, one JSON object per line |
 | `data/deploys.json` | Recent deploys, with the service, owning team, time, and change |
@@ -29,7 +27,7 @@ You need a Google Cloud project with billing enabled.
 ```bash
 gcloud config set project YOUR_PROJECT_ID
 gcloud services enable aiplatform.googleapis.com
-git clone https://github.com/nextwork-projects/langgraph-incident-triage.git ~/langgraph-incident-triage-agents
+git clone https://github.com/mahendrayadavali/langgraph-incident-triage-agents.git ~/langgraph-incident-triage-agents
 cd ~/langgraph-incident-triage-agents
 python3 -m venv .venv
 source .venv/bin/activate
@@ -49,8 +47,3 @@ You should see `WORKFLOW PAUSED` and an approval payload. The `LangChainBetaWarn
 ## Cost
 
 Each run makes a few Gemini 3.7 Flash calls, which costs a few cents at most. Cloud Shell is free.
-
-## Branches
-
-- `main` is the starting point for the Project. Clone it and follow the Project's steps from here.
-- `solution` is the finished build, with offline tests (`python3 -m pip install pytest && python3 -m pytest`). Use it to check your work if you get stuck.
-- 
2.43.0