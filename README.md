# AI Starter Platform

> **Build AI that thinks in patterns, not prompts.**

---

## The Problem

You've seen the demos. ChatGPT answering questions. Copilot writing code. 

But when you try to build something real — something that *does* work, not just *talks* about work — you hit a wall.

**One prompt isn't enough.**

Real tasks need:
- Steps that build on each other
- Multiple perspectives working together  
- Routing to the right specialist
- Iteration until it's actually good

This is **Agentic AI** — AI that acts, not just responds.

---

## The Five Patterns

Every complex AI system is built from five primitives.

Like DNA has four bases but creates all life, these five patterns create all agentic behavior:

| Pattern | What It Does | When to Use |
|---------|--------------|-------------|
| **Chain** | A → B → C → D | When steps depend on previous output |
| **Parallel** | A ∥ B ∥ C → combine | When you need multiple perspectives fast |
| **Router** | classify → route → specialist | When different inputs need different handling |
| **Orchestrator** | break down → workers → combine | When tasks are too complex for one agent |
| **Evaluator** | generate → evaluate → refine → loop | When "good enough" isn't good enough |

**That's it.** Five patterns. Every agentic system you've seen — AutoGPT, CrewAI, LangGraph — is a combination of these.

---

## See It Work

```bash
# 1. Clone
git clone git@github.com:InventorSingh/ai-starter-platform.git
cd ai-starter-platform

# 2. Set your key
export OPENAI_API_KEY=your-key-here

# 3. Start infrastructure
docker compose up -d

# 4. Run
./mvnw spring-boot:run

# 5. Open
open http://localhost:8080/agentic-workflows
```

Login: `admin` / `password`

---

## The Patterns, Explained

### 1. Chain — One Thing Leads to Another

```
Input → Analyze → Identify Audience → Suggest Improvements → Summarize
```

Each step receives the output of the previous step. Like a relay race — the baton passes forward.

**Use when:** Writing pipelines, data transformation, progressive refinement.

```java
String result = input;
for (String prompt : prompts) {
    result = chatClient.prompt(prompt + result).call().content();
}
return result;
```

---

### 2. Parallel — Many Eyes See More

```
         ┌→ Technical Analysis  ─┐
Input  ──┼→ Business Analysis   ─┼→ Combined Report
         ├→ UX Analysis         ─┤
         └→ Risk Analysis       ─┘
```

Same input, different lenses, combined insight. Like asking four experts the same question.

**Use when:** You need speed + breadth. Multiple perspectives on one problem.

```java
List<CompletableFuture<String>> futures = perspectives.stream()
    .map(p -> CompletableFuture.supplyAsync(() -> 
        chatClient.prompt(p + input).call().content()))
    .collect(toList());

return futures.stream().map(CompletableFuture::join).collect(toList());
```

---

### 3. Router — Right Tool, Right Job

```
Input → Classify → { technical? → Tech Expert
                     business?  → Business Analyst  
                     creative?  → Creative Pro }
```

Not all problems are the same. Route to the specialist who knows best.

**Use when:** Mixed input types, specialized expertise needed.

```java
String category = chatClient.prompt("Classify: " + input).call().content();
String specialist = routes.get(category);
return chatClient.prompt(specialist + input).call().content();
```

---

### 4. Orchestrator-Workers — Divide and Conquer

```
                    ┌→ Worker 1 (subtask A) ─┐
Task → Orchestrator ┼→ Worker 2 (subtask B) ─┼→ Combined Result
                    └→ Worker 3 (subtask C) ─┘
```

Complex task? Break it down. Assign to specialists. Combine results.

**Use when:** Tasks too big for one prompt. Need coordination.

```java
List<String> subtasks = orchestrator.breakDown(task);
List<String> results = workers.processInParallel(subtasks);
return combine(results);
```

---

### 5. Evaluator-Optimizer — Good Enough Isn't

```
Generate → Evaluate → "Score: 6/10, improve X" → Refine → Evaluate → "Score: 9/10" → Done
```

First draft is rarely best. Evaluate. Improve. Repeat until satisfied.

**Use when:** Quality matters more than speed. Creative work. Complex solutions.

```java
String solution = generate(task);
for (int i = 0; i < maxIterations; i++) {
    Evaluation eval = evaluate(solution);
    if (eval.score >= threshold) break;
    solution = refine(solution, eval.feedback);
}
return solution;
```

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    AI Starter Platform                   │
├─────────────────────────────────────────────────────────┤
│  UI Layer          │  Thymeleaf + HTMX                  │
│  API Layer         │  Spring MVC + REST                 │
│  AI Layer          │  Spring AI + ChatClient            │
│  Workflow Layer    │  5 Pattern Implementations         │
│  Memory Layer      │  Neo4j (conversation) + PgVector   │
│  Observability     │  Micrometer → Prometheus → Grafana │
└─────────────────────────────────────────────────────────┘
```

---

## What's Included

| Component | Purpose |
|-----------|---------|
| `WorkflowService.java` | All 5 patterns, production-ready |
| `ChatClient` config | Memory + RAG + Tools wired up |
| Docker Compose | PostgreSQL + Neo4j + Prometheus |
| Interactive UI | Test workflows in browser |
| MCP Server (demo) | Model Context Protocol example |

---

## Extend It

**Add a new pattern:**
1. Add method to `WorkflowService.java`
2. Add endpoint in `WorkflowApiController.java`
3. Add UI card in `agentic-workflows.html`

**Add tools:**
```java
@Tool("Description of what this tool does")
public String myTool(@ToolParam("param description") String input) {
    return doSomething(input);
}
```

**Add memory:**
Neo4j stores conversation history. PgVector stores documents for RAG.

---

## The Philosophy

> **Patterns over prompts.**

Prompts are fragile. They break when context changes.

Patterns are durable. They work because they match how work actually flows.

Learn the five patterns. Combine them. Build systems that think.

---

## Links

- [Spring AI Documentation](https://docs.spring.io/spring-ai/reference/)
- [Anthropic's Agentic Patterns](https://www.anthropic.com/research/building-effective-agents)
- [Model Context Protocol](https://modelcontextprotocol.io/)

---

**Built for learning. Ready for production.**
