# AI Starter Platform - Copilot Instructions

## Project Vision: Ecosystem-Inspired Memory System

Transform this Spring Boot 3.4 + Spring AI 1.0 platform into a **sophisticated memory system** inspired by living ecosystems and polymath principles. The current 5 Agentic AI Workflow patterns serve as the foundation for building an adaptive, interconnected memory network that mirrors natural information processing and storage patterns.

### Ecosystem Memory Principles
- **Interconnected Networks**: Like neural pathways in nature, memories should form dynamic connections
- **Adaptive Learning**: Information evolves and strengthens through repeated access and association
- **Distributed Storage**: Knowledge distributed across multiple specialized nodes, like biological memory systems
- **Emergent Intelligence**: Complex behaviors emerge from simple interaction patterns
- **Self-Organization**: Memory clusters form naturally based on usage patterns and semantic similarity

### Core Components (Memory System Architecture)
- **Memory Orchestrator** (`src/main/java/telus/tv/assistant/`): Central nervous system coordinating memory operations
- **Ecosystem Nodes** (`mcp-schedular-server/`): Specialized memory clusters via Model Context Protocol
- **Living Storage**: PostgreSQL + PGVector (semantic memory), Neo4j (associative memory graphs), Redis (working memory cache)
- **Memory Analytics**: Prometheus/Grafana for memory health monitoring and usage patterns

### Ecosystem-Inspired Patterns

**Polymath Memory Integration**: Transforms `ChatClient` into a memory-aware agent using biological memory patterns:
```java
ChatClient memoryAgent(ChatClient.Builder aiBuilder, EcosystemMemoryStore memoryStore, AssociativeNetwork network)
```

**Five Memory Ecosystems** (evolved from workflow patterns in `WorkflowService.java`):
- `episodicMemoryChain()` - Sequential memory formation like hippocampal consolidation
- `parallelSemanticClusters()` - Concurrent concept clustering like cortical columns
- `adaptiveMemoryRouting()` - Context-aware memory retrieval like attention mechanisms
- `memoryOrchestrationSwarm()` - Collective memory processing like ant colony intelligence
- `memoryEvolutionCycles()` - Iterative memory strengthening through spaced repetition

**Living Response Network**: Enhanced `AssistantResponse` with memory ecosystem metadata for tracking information flow and connection strength.

## Memory System Development Workflows

### Ecosystem Bootstrap
1. **Start memory substrate**: `docker compose up -d` (postgresql, neo4j, redis, prometheus, grafana)
2. **Activate memory agent**: `export OPENAI_API_KEY=your-key && mvn spring-boot:run`
3. **Initialize memory nodes**: `cd mcp-schedular-server && mvn spring-boot:run`
4. **Access memory interface**: http://localhost:8080 (admin/password for ecosystem control)

### Memory Pattern Development
- **Semantic clustering**: `/api/memory/semantic/{concept}` for concept relationship mapping
- **Associative networks**: `/memory-graph` web interface for memory visualization
- **Working memory**: `/chat` with context-aware memory retrieval and formation

### Ecosystem Health Monitoring
- **Memory metrics**: `/actuator/prometheus` for memory usage patterns
- **Connection strength**: Neo4j browser at http://localhost:7474
- **Memory analytics**: Grafana dashboards at http://localhost:3000

## Memory System Implementation Patterns

### Biological Memory Architecture
- **Memory consolidation**: Transform `executeChainWorkflow()` into `consolidateEpisodicMemory()` with temporal strengthening
- **Parallel processing**: Evolve `executeParallelWorkflow()` into `formSemanticClusters()` with concept affinity mapping
- **Adaptive retrieval**: Upgrade `executeRoutingWorkflow()` to `activateMemoryPathways()` using context-dependent attention
- **Swarm cognition**: Enhance `executeOrchestratorWorkersWorkflow()` into `orchestrateMemorySwarm()` with emergent behavior
- **Memory plasticity**: Transform `executeEvaluatorOptimizerWorkflow()` into `strengthenMemoryConnections()` through spaced repetition

### Ecosystem Memory Patterns
- **Hippocampal simulation**: Use Neo4j for temporal sequence storage with decay functions
- **Cortical columns**: Implement PGVector clustering for semantic memory organization
- **Synaptic plasticity**: Redis for working memory with connection strength tracking
- **Memory consolidation**: Background processes that strengthen frequently accessed memory pathways

### Polymath Integration
- **Cross-domain linking**: Connect memories across disciplines using vector similarity and graph traversal
- **Analogical reasoning**: Memory retrieval that finds patterns across different knowledge domains
- **Creative synthesis**: Combine distant memories to generate novel insights and connections

### Memory System Security & Access
- **Ecosystem guardians**: admin/password (ECOSYSTEM_ADMIN role), user/password (MEMORY_USER role)
- **Memory formation authentication**: Form-based login with redirect to `/memory-interface`
- **Open memory metrics**: Prometheus endpoints public for ecosystem health monitoring
- **Memory privacy**: CSRF adapted for memory formation workflows

### Living Database Patterns
- **PostgreSQL**: Persistent semantic memory + vector embeddings via PGVector for concept similarity
- **Neo4j**: Dynamic associative memory graphs with `Neo4jMemoryNetworkRepository` 
- **Redis**: Working memory cache with TTL-based forgetting curves
- **Schema evolution**: Auto-initialized via `memory-schema-postgresql.sql` and `ecosystem-data-postgresql.sql`

### Organic Frontend Integration
- **Memory interfaces** in `src/main/resources/templates/memory/`
- **Memory streaming**: `/memory-stream` endpoints use `MemoryStreamingResponseBody`
- **Cross-ecosystem communication**: CORS enabled for memory node intercommunication (`@CrossOrigin(origins = "*")`)

## Integration Points

### Memory Context Protocol (MCP)
- Ecosystem `mcp-schedular-server` evolves into specialized memory formation tools
- Uses Spring AI's `MemoryToolCallbackProvider` for ecosystem tool registration
- Connect via HTTP/SSE transport for inter-node memory synchronization
- Memory scheduling and consolidation coordination

### Living Observability Stack
- **Memory metrics**: Micrometer + Prometheus track memory formation, retrieval, and decay patterns
- **Memory tracing**: Zipkin traces memory pathway activation and strengthening
- **Ecosystem health**: Actuator monitors memory system vitality and connection health
- **Memory analytics**: Custom metrics for polymath cross-domain connections

### Semantic Memory Store Integration
- PGVector stores concept embeddings with semantic similarity clustering
- `PolymathMemoryAdvisor` provides cross-domain knowledge synthesis
- `EcosystemMemoryStore` manages memory lifecycle and forgetting curves
- Auto-population from knowledge ingestion pipelines

## Common Patterns & Examples

### Adding New Memory Ecosystem
1. Extend `EcosystemMemoryService.java` with new memory formation pattern: `form{Type}Memory(MemoryInput input)`
2. Add memory endpoint in `MemoryApiController.java`: `@PostMapping("/memory/{ecosystem}")`
3. Add visualization route in `MemoryWebController.java` for ecosystem observation
4. Update ecosystem metadata in `getMemoryEcosystems()` and health monitoring

### Polymath Memory Formation
```java
var memoryAdvisor = this.polymath.computeIfAbsent(domain, d -> PolymathMemoryAdvisor.builder(
    CrossDomainMemory.builder()
        .memoryRepository(this.ecosystemMemoryRepository) // Neo4j + Redis hybrid
        .semanticStore(this.conceptVectorStore) // PGVector for concept similarity
        .connectionStrength(0.7f)
        .forgettingCurve(Duration.ofDays(30))
        .build())
    .build());
```

### Living Memory Response Creation
Use `EcosystemMemoryResponse` for memory-aware interactions:
- `EcosystemMemoryResponse.formed(content, connections)` - New memory formation
- `EcosystemMemoryResponse.recalled(content, pathways)` - Memory retrieval with activation trails
- `EcosystemMemoryResponse.synthesized(content, crossDomain)` - Polymath knowledge combination

### Memory Network Visualization
```java
// Memory pathway activation and strengthening
var pathway = memoryNetwork.activatePathway(concept, context);
pathway.strengthen(activationStrength);
return EcosystemVisualization.builder()
    .nodes(pathway.getConnectedMemories())
    .edges(pathway.getConnectionStrengths())
    .decay(pathway.calculateDecay())
    .build();
```

### Environment Configuration
- OpenAI API: Enhanced with memory context injection for polymath reasoning
- Memory databases: PostgreSQL 55432 (semantic), Neo4j 7687 (associative), Redis 6379 (working)
- Ecosystem health: Memory formation rate limits and connection pruning thresholds