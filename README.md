First attempt at a solution. Incomplete. Room left for agentic-code review as per specifications to improve upon(mentioned at the end of the notebook).

Find the course files at the link below :

https://www.kaggle.com/learn-guide/5-day-agents

Associated Writeup:


AI-Driven HR Automation Platform Using Google ADK + Model Context Protocol (MCP)
A Multi-Agent Workflow for Context-Aware HR Operations
Problem Statement
Human Resources (HR) is the backbone of organizational efficiency, culture, and compliance. Despite the strategic importance of (HR), many operations remain highly manual, repetitive, and error-prone, relying on multi-step processes that require significant human oversight. Tasks such as onboarding new employees, managing access as roles change, retrieving policy information, generating legal or compliance documents, conducting internal audits, handling leave requests, and orchestrating offboarding are inherently context-sensitive, multi-step, and time-critical, requiring precision, accuracy, and timely execution.

These workflows span multiple platforms, including HRIS systems, emails, spreadsheets, shared documents, asset tracking tools, and communication channels. HR teams spend excessive time navigating systems rather than delivering strategic value. Manual coordination introduces risk: missed provisioning steps, delayed approvals, outdated policy versions, inconsistent documents, and potential compliance violations, all of which can have significant operational or legal impact.

The inefficiency directly affects the employee experience. New hires may wait hours or days for essential accounts or access to systems. Employees struggle to locate up-to-date policy information, while managers experience delays in routine HR operations. These friction points reduce productivity, lower morale, and potentially create compliance or legal risks.

Organizations require a context-aware automation layer that reduces operational friction, delivers accurate and timely responses, maintains workflow continuity, and adapts dynamically to changes in HR processes while supporting strategic HR initiatives.

The Model Context Protocol (MCP) provides the foundation for enabling AI agents to maintain, share, and reason over rich contextual memory. MCP allows agents to automate complex HR processes while preserving knowledge of prior actions, session history, and inter-agent collaboration. With MCP, AI agents can operate in a more human-like, contextually intelligent manner, bridging gaps in traditional automation and ensuring operational consistency across HR functions.

Why AI Agents + MCP?
HR operations are inherently multi-actor, multi-stage, and highly context-dependent. Traditional rule-based automation breaks down under unexpected conditions, workflow changes, or exception handling. By leveraging AI agents equipped with MCP, organizations achieve automation that is both robust and flexible, able to adapt to unforeseen circumstances while maintaining high reliability.

MCP enhances AI agents through:

Context Engineering: Structured design of context objects allows agents to store, retrieve, and reason over relevant workflow data, ensuring accurate task execution at every step.
Sessions & Memory: Agents retain session-specific state, such as prior approvals, employee role history, and previously answered queries, enabling continuity across multiple interactions.
Agent Interoperability: MCP enables agents to dynamically share contextual data, supporting collaborative decision-making across HR, IT, compliance, and other departments.
Adaptive Decision-Making: Context-aware agents can resolve exceptions autonomously, escalate unresolved issues intelligently, and maintain workflow continuity without human intervention.
Event-Driven Operation: Agents react to triggers like new hires, role changes, policy updates, compliance events, or leave requests, ensuring timely and accurate outcomes.
A2A (Agent-to-Agent) Communication for Context Sharing
While MCP provides each agent with session-specific memory, many HR workflows require real-time collaboration across multiple agents. A2A (Agent-to-Agent) communication ensures that agents can share relevant context efficiently:

Seamless Context Sharing: Agents exchange session memory, employee context, workflow states, and prior approvals, preventing redundant actions.
Dynamic Collaboration: For example, the Onboarding Agent notifies the Access Management Agent and Document Generation Agent about a new hire, sharing all necessary context in real time.
Error Handling and Escalation: If an agent encounters an exception, it escalates context-aware alerts to the relevant agent, enabling automated recovery.
Multi-Agent Orchestration: The Workflow Orchestration Agent coordinates multiple agents, maintains workflow continuity, and ensures multi-step processes complete successfully.
Efficiency and Consistency: By sharing context directly, agents avoid redundant actions, maintain accurate data, and ensure consistent responses across HR, IT, compliance, and departmental operations.
Together, MCP + A2A enables agents to retain individual memory and reason collectively, making HR automation truly context-aware and collaborative.

Built-In Tools and Function Tools
The platform leverages built-in Google Workspace tools as deterministic FunctionTools, optionally wrapped as AgentTools for NLP-driven access. These tools integrate seamlessly with MCP to share context and trigger agent actions:

Google Calendar Tool (CalendarTool) – Automates scheduling for onboarding, interviews, training, and feedback meetings. Integrated with Onboarding Agent, Recruitment Agent, and Performance & Feedback Agent. Context stored in MCP for conflict resolution and orchestration.
Gmail Tool (EmailTool) – Sends HR notifications, reminders, and approval requests. Used by Leave & Attendance Agent, Onboarding Agent, and Compliance Monitoring Agent. Logs all emails in MCP session memory.
Google Drive / Document Tool (DocumentTool) – Accesses templates, stores generated documents, or retrieves policies. Core for Document Generation Agent and Policy Update & Audit Agent. Updated documents are registered in MCP for inter-agent access.
Custom FunctionTools are also included for specialized tasks such as:

Policy compliance checks
Asset assignment
Leave balance calculation
AgentTools and LLM Agents
Some agents are exposed as AgentTools so they can be invoked by other agents:

Knowledge Retrieval AgentTool – Allows other agents to query policies or historical context in natural language.
Retention & Turnover Prediction AgentTool – Calls a machine learning model inference API to provide context-aware retention risk scores.
Career Development AgentTool – Provides training or mobility suggestions for other agents.
These AgentTools, along with FunctionTools, are registered with the MCP server, enabling cross-agent context sharing, orchestration, and memory-driven decision-making.

All Agents in the Context-Aware Multi-Agent Workflow
Onboarding Agent – Manages candidate context, prior communications, IT provisioning, departmental requirements, and workflow history.
Offboarding Agent – Coordinates account deactivation, asset return, exit documents, and payroll compliance.
Knowledge Retrieval AgentTool – Answers policy questions and provides guidance via prior context.
Document Generation Agent – Creates offer letters, NDAs, and employment contracts, using DocumentTool and templates.
Access Management Agent – Provisions/deprovisions accounts, integrates with CalendarTool and EmailTool for scheduling and notifications.
Compliance Monitoring Agent – Tracks trainings, escalates overdue actions, maintains audit trail.
Workflow Orchestration Agent – Coordinates triggers, task sequencing, A2A communication, and error handling.
Leave & Attendance Agent – Handles leave requests, approvals, balance checks, integrating with EmailTool for notifications.
Recruitment Agent – Screens resumes, schedules interviews via CalendarTool, and maintains candidate context.
Performance & Feedback Agent – Automates OKR reminders, 360° feedback collection, and review cycles.
IT Asset Lifecycle Agent – Tracks and assigns company assets, coordinating with offboarding and access management.
Sentiment & Well-Being Agent – Analyzes anonymized employee communications and surveys.
Career Development AgentTool – Recommends training and career paths for other agents.
Policy Update & Audit Agent – Monitors policy versions and propagates updates across agents.
Department Interaction Agent – Functions as an AI manager for each department, customizing workflows based on shared context.
Retention & Turnover Prediction AgentTool – Provides ML-based retention risk scores to HR, Onboarding, and Workflow Orchestration agents.
All agents are autonomous, modular, context-aware, and interconnected through A2A communication, enabling complex workflows to execute efficiently.

Demo Overview
Automated Onboarding – CalendarTool schedules sessions, Onboarding Agent coordinates IT provisioning, DocumentTool generates contracts, EmailTool sends notifications.
Natural-Language HR Assistant – Knowledge Retrieval AgentTool responds to queries using session and historical context.
Retention Risk Prediction – Retention & Turnover Prediction AgentTool provides scores for proactive HR interventions.
Performance & Feedback Automation – CalendarTool schedules feedback cycles, EmailTool sends reminders, Performance Agent collects responses.
Compliance Automation – Compliance Monitoring Agent tracks training deadlines, escalates via EmailTool, and records in MCP memory.
Cross-Agent Scenario Handling – MCP context allows agents to detect conflicts, such as previous contractors returning, and adjust workflows automatically.
Agent Quality, Debugging, and Evaluation
Observation – Real-time monitoring of agent decisions.
Logging – Detailed session logs, tool calls, and notifications stored in MCP.
Tracing – Track multi-agent interactions for debugging and root-cause analysis.
Metrics – Task completion rates, SLA adherence, response latency, and error frequency.
Evaluation – Automated test workflows, scenario simulations, and human-in-the-loop validation.
The Build
Event-Driven Triggers – Workflows start on new hires, offboarding, role changes, or compliance events.
Agent Communication Pipelines – A2A context sharing coordinated via MCP.
Context Persistence – All session memory, approvals, scheduled events, and generated documents retained in MCP.
Integration – Built-in support for CalendarTool, EmailTool, DocumentTool, HRIS systems, and ML inference APIs.
Internal Databases – State tracking, workflow history, and auditing records.
Agents are autonomous, modular, and interoperable, enabling dynamic scaling, seamless collaboration, and adaptive workflow evolution.

If I Had More Time
Predictive Analytics – ML-driven retention, onboarding success, and performance insights.
Expanded AI Manager Capabilities – Department-level oversight and workflow reasoning.
Multilingual Support – Global HR automation with consistent context across languages.
Workforce Planning Dashboards – Visualize resource allocation, talent gaps, and productivity metrics.
Real-Time Multi-Country Compliance Tracking – Ensure global HR policies and regulatory adherence.
Unified IT + HR + Ops Helpdesk – Context-aware session memory for faster issue resolution.
Multimodal Capabilities – Parse documents, extract structured data, and integrate with external knowledge bases.
Simulation & Scenario Modeling – Test workflows and evaluate potential bottlenecks before production deployment.
This creates an end-to-end, intelligent HR automation ecosystem, leveraging MCP + A2A, FunctionTools, AgentTools, and built-in Google Workspace integrations for maximum efficiency, compliance, and employee satisfaction.
