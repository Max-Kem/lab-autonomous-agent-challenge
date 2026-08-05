# Architect the bot someone will actually pay for

> **How you'll submit this lab**
>
> This repo is your lab. Fork it, do the work described below in your fork, then open a pull
> request back into this repository. An AI reviewer will check your PR against `rubric.md` and
> leave feedback directly on the PR. See `README.md` for the full workflow.

## Learning Goal

You will build one Autonomous Agent Challenge workflow path and prove data moves from input to output correctly.

## Working Context

This lab turns a manual handoff into a small automated workflow.
You define one input, one transformation, and one output a reviewer can inspect.
Avoid broad automation. Prove the critical path first.

## Proof of Learning

Submit one `lab_proof.md` with the workflow export or configuration, one execution trace, one input payload, and one output record.

## Pseudocode

```text
INPUT: source event, message, ticket, or payload
DECIDE: required fields, routing rule, and destination
BUILD: trigger -> transform -> action
VERIFY: inspect one successful run and output artifact
EXPLAIN: justify the mapping and operational risk
```

## Prompt Discipline

Use AI for review, debugging, or critique. Do not ask it to produce the final artifact or final answer.

```text
Role: Workflow reviewer
Task: Challenge my event-flow plan before I build or submit.
Inputs: trigger, sample payload, destination schema, and proof plan.
Constraints: Do not build the workflow for me. Find brittle mappings and missing checks.
Output format: three workflow risks, two trace checks, and one simplification.
Verification: Name the execution evidence that proves the workflow ran.
```

## Build

## Step-by-Step Instructions

### Part 1: Planning (Required)

#### Step 1: Select a Use Case

Do: Choose a real-world problem that an autonomous agent could solve. Tip: if you have a hard time getting started, ask an LLM to choose one for you.

Do:
1. **Review use case options** (or propose your own):

**Option A: Customer Support Agent**
- Automatically answer customer questions using company knowledge base
- Escalate complex issues to human agents
- Track conversation history and satisfaction

**Option B: Research Assistant**
- Automatically research topics and compile summaries
- Answer questions based on multiple sources
- Track research history and sources

**Option C: Document Q&A System**
- Answer questions about internal company documents
- Support multiple document types (PDFs, Word, web pages)
- Provide citations and source tracking

**Option D: Lead Qualification Agent**
- Qualify leads from website forms or emails
- Ask follow-up questions to understand needs
- Route qualified leads to appropriate sales team

**Option E: Your Own Idea**
- Propose a use case relevant to your interests or work
- Ensure it requires autonomous agent capabilities (not just simple automation)

2. **Select one use case** and document:
   - **Problem statement:** What problem does this solve?
   - **Target users:** Who will use this agent?
   - Verify: How do we know it's working?
   - **Current process:** How is this done manually today?

---

#### Step 2: Apply Technology Selection Framework

Do: Determine which technologies are needed for your use case.

Do:
1. **Answer these questions for your use case:**

**Does it need external knowledge?**
- [ ] Yes to Needs RAG
- [ ] No to Can use LLM knowledge only

**Does it need to interact with external systems?**
- [ ] Yes to Needs tools/integrations (LangChain tools or n8n)
- [ ] No to Can be standalone

**Does it need multi-step reasoning?**
- [ ] Yes to Consider LangGraph for structured workflows
- [ ] No to Simple LangChain agent might suffice

**Does it need to integrate with business systems?**
- [ ] Yes to n8n for orchestration and integrations
- [ ] No to Can be standalone Python application

**Does it need to be autonomous (run without human input)?**
- [ ] Yes to Needs scheduling, error handling, monitoring
- [ ] No to Can be on-demand only

2. **Document your technology stack:**
   - **Core LLM:** (OpenAI, Anthropic, etc.)
   - **RAG components:** (Vector DB, embeddings, chunking strategy)
   - **Agent framework:** (LangChain, LangGraph, or custom)
   - **Orchestration:** (n8n, custom scheduler, or none)
   - **Tools/integrations:** (What external systems does it need?)

3. **Justify your choices:**
   - Why did you choose these technologies?
   - What alternatives did you consider?
   - What are the trade-offs?

---

#### Step 3: Define MVP Scope

Do: Define the minimum viable product - the smallest version that delivers value.

Do:
1. **List all possible features** for your agent (brainstorm everything)

2. **Categorize features:**
   - **Must-have (MVP):** Core functionality that solves the main problem
   - **Should-have (v2):** Important but not critical for first version
   - **Nice-to-have (v3+):** Enhancements for future versions

3. **Define MVP boundaries:**
   - **What's included:** List all MVP features
   - **What's excluded:** List what's explicitly out of scope
   - **Success metrics:** How will you measure MVP success?

**Example MVP scope:**
```
MVP Features:
- Answer questions from knowledge base (RAG)
- Support PDF documents only
- Single language (English)
- Basic conversation memory
- Simple web interface

Out of Scope (v2+):
- Multi-language support
- Multiple document types
- Advanced analytics
- Mobile app
- Integration with CRM
```

---

#### Step 4: Assess Risks and Mitigation

Do: Identify potential problems and plan how to address them.

Do:
1. **Identify risks** in these categories:

**Technical Risks:**
- API rate limits or costs
- Model accuracy/hallucination
- Integration failures
- Performance issues

**Business Risks:**
- User adoption
- Change management
- Cost overruns
- Scope creep

**Data Risks:**
- Data quality
- Privacy/security
- Data availability
- Bias in training data

2. **For each risk, document:**
   - **Risk description:** What could go wrong?
   - **Probability:** High, Medium, Low
   - **Impact:** High, Medium, Low
   - **Mitigation strategy:** How will you prevent or handle it?

**Example risk assessment:**
```
Risk: High API costs from excessive LLM calls
Probability: Medium
Impact: High
Mitigation:
- Implement caching for common queries
- Use cheaper models for simple tasks
- Set up cost monitoring and alerts
- Optimize prompts to reduce token usage
```

---

#### Step 5: Create Project Plan

Do: Document your complete project plan.

Do:
1. **Create a project plan document** with these sections:

**Project Overview:**
- Use case description
- Target users
- Verification criteria

**Technology Stack:**
- Selected technologies
- Justification for choices
- Alternatives considered

**MVP Scope:**
- Included features
- Excluded features
- Success metrics

**Risk Assessment:**
- Identified risks
- Mitigation strategies

**Implementation Phases:**
- Phase 1: Setup and data preparation
- Phase 2: Core agent development
- Phase 3: Integration and testing
- Phase 4: Deployment and monitoring

**Timeline:**
- Estimated time for each phase
- Key milestones
- Dependencies

**Resources Needed:**
- Team members and roles
- Tools and services
- Budget considerations

2. **Use this template structure:**

```markdown
# Autonomous Agent Project Plan

## 1. Use Case
[Describe your selected use case]

## 2. Technology Stack
[Document your technology choices and justifications]

## 3. MVP Scope
[Define what's in and out of scope]

## 4. Risk Assessment
[Identify risks and mitigation strategies]

## 5. Implementation Plan
[Break down into phases with timeline]

## 6. Success Metrics
[How will you measure success?]
```

---

### Part 2: Optional Simple Implementation

#### Step 6: Build Minimal Prototype

Do: Create a simple prototype to validate your plan.

Do:
1. **Choose the simplest possible implementation** of your MVP:
   - Use the most basic version of each technology
   - Focus on core functionality only
   - Skip advanced features

2. **Build a minimal prototype:**
   - **If using RAG:** Simple document Q&A with one PDF
   - **If using LangChain:** Basic agent with 1-2 tools
   - **If using n8n:** Simple workflow with manual trigger
   - **If using LangGraph:** Minimal state machine with 2-3 nodes

3. **Test the prototype:**
   - Verify core functionality works
   - Identify any technical challenges
   - Document what you learned

4. **Update your project plan:**
   - Note any changes needed based on prototype
   - Adjust timeline if necessary
   - Update risk assessment

**Example minimal prototype:**
- Single PDF document in vector database
- Simple LangChain agent with RAG
- Basic question-answering interface
- No integrations, no scheduling, no error handling (yet)

---

## Submission Guidelines


## Extension Activities (Optional)

1. **Detailed technical design:**
   - Create architecture overviews
   - Design data movement
   - Specify API contracts
   - Define data models

2. **Cost analysis:**
   - Estimate API costs
   - Calculate infrastructure costs
   - Compare different technology options
   - Create budget projection

3. **Full prototype:**
   - Build complete MVP (not just minimal)
   - Implement all core features
   - Add error handling and monitoring
   - Deploy to staging environment

4. **User research:**
   - Interview potential users
   - Validate use case assumptions
   - Gather feedback on MVP scope
   - Refine project plan based on feedback

5. **Deployment planning:**
   - Design deployment architecture
   - Plan monitoring and logging
   - Define rollback procedures
   - Create runbook for operations

---

## Resources

- [LangChain Use Cases](https://docs.langchain.com/use_cases/)
- [LangGraph Patterns](https://langchain-ai.github.io/langgraph/tutorials/)
- [RAG Implementation Guide](https://www.pinecone.io/learn/retrieval-augmented-generation/)
- [n8n Use Cases](https://n8n.io/use-cases/)
- [Project Planning Templates](https://www.atlassian.com/software/confluence/templates/project-plan)

---

## Troubleshooting

**Issue:** Can't decide on use case
- **Solution:** Start with a problem you understand well, choose something with clear verification criteria, pick a use case that's not too complex for your first project

**Issue:** Technology selection unclear
- **Solution:** Start simple (basic LangChain agent), add complexity only if needed, refer to module-3 lessons on when to use each technology, ask: "What's the simplest solution that works?"

**Issue:** MVP scope too large
- **Solution:** Cut features aggressively, focus on one core user journey, remember: MVP should take days/weeks, not months, you can always add features later

**Issue:** Can't identify risks
- **Solution:** Think about what could go wrong technically, consider business/user adoption risks, research similar projects that failed, ask: "What assumptions am I making?"

**Issue:** Project plan feels incomplete
- **Solution:** That's okay - plans evolve, focus on the next phase in detail, leave later phases as high-level, update plan as you learn more

## Verify

The reviewer can inspect one run trace and see the observable output in the destination.

## Explain

What is the first failure mode you would monitor if this workflow ran daily?

## Submission Sanity Check

Before you submit:
- Keep only files for this lab.
- Name files clearly.
- Remove secrets, API keys, tokens, and unrelated data.
- Make `lab_proof.md` the entry point for the reviewer.

## Optional Stretch

- Add one operational control: retry handling, error notification, duplicate detection, audit logging, or a second route.
- Create a small UI with vibecoding only if it safely submits or previews the workflow input. Deploy only if no credentials are exposed.
