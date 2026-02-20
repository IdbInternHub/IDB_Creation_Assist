# IDB_Creation_Assist

Dashboard creation assistant 

Version: 1.0 

Date: February 2026 

Status: Initial Phase [ On date: 19-02-2026] 

 1. EXECUTIVE SUMMARY 

This system provides intelligent, step-by-step guidance for dashboard creation. Each step has detailed documentation including "what to do", prerequisites, common pitfalls, and code examples. When users ask contextual questions (e.g., "How to load frame with pre-filters?"), the system: 
 
1. Understands the question intent and maps it to relevant steps 
2. Identifies where in the workflow this action belongs 
3. Checks if prerequisites are met 
4. Explains WHEN and WHERE to perform the action 
5. Provides detailed guidance specific to that step 
 
The system maintains step documentation as structured data and uses AI to answer queries contextually within the workflow. 

2. Core Concept: Step-Centric Documentation 

2.1 Problem Being Solved 

User asks: "How do I load the frame with pre-filters?" 

Traditional answer: Generic how-to without workflow context 

Better answer: Identify this is Step 4 action → Explain when to do it → Provide step-specific guidance 

 

2.2 Solution: Step-Based Architecture 

Every step in dashboard creation has: PURPOSE, ACTIONS, PREREQUISITES, OUTPUTS, QUESTIONS, and EXAMPLES. When user queries arrive, map them to steps and answer within a step context. 

3. Query Resolution System 

3.1 How Queries Map to Steps 

User Query → AI Mapping → Identify Step(s) → Check Prerequisites → Provide Answer 

Example Query Resolution Flow 

Scenario: User Asks Pre-Filter Question (sample) 

User Input: "How do I load the frame with pre-filters?" 

AI Analysis: Extract keywords: "load", "frame", "pre-filters" 

Step Mapping: Maps to Step 4 (Filters & Parameters) with 95% confidence 

Prerequisite Check: Has user completed Step 2 (Data Source)? Check user session 

If Prerequisites Met: Return full Step 4.3-4.6 guidance on pre-filters 

If Prerequisites Missing: Say: "To add filters, first complete Step 2 (Select Data Source). Want me to guide you there?" 

Clarifying Questions: "Are you using Tableau, Power BI, or another tool?" → Tailor response 

Response Generated: Combination of: Step 4 context + Pre-filter explanation + Code example + Pro tips 

4. Technical Architecture 

Core Components 

Prepare stepper screen documentation with purpose, pre-requisite. 

Component 

Function 

Implementation 

Step Database 

Store step definitions (purpose, actions, prerequisites, FAQ) 

JSON with step documents 

Query Mapper 

Map user queries to steps (semantic similarity) 

Sentence embeddings + similarity search 

Prerequisite Validator 

Check if user can access step content 

 simple rule engine 

Response Generator 

Create contextual answers combining step data + LLM 

LLM 

User Session Tracker 

Remember completed steps, current context 

session storage 

Context Engine 

Maintain awareness of user position in workflow 

Session state management 

 

Data Flow Diagram 

USER QUERY INPUT 
      ↓ 
[Query Mapper] - Extract keywords, create embedding 
      ↓ 
[Step Database] - Find similar steps by embedding similarity 
      ↓ 
[Prerequisite Validator] - Check: Can user access these steps? 
      ↓ 
[Context Engine] - Determine user's current step (from session) 
      ↓ 
IF prerequisites met: 
   ↓ 
   [Response Generator] - Combine step template + LLM guidance 
   ↓ 
   [Format Response] - Apply template + examples + pro tips 
ELSE: 
   ↓ 
   [Suggest Prerequisites] - "Complete Step X first" 
      ↓ 
SEND RESPONSE TO USER 
      ↓ 
[Session Tracker] - Update user progress/context 

10. TIMELINE & MILESTONES 

Phase 1 - Requirements & Architecture Design: 2 weeks 

Phase 2 - Core Development: 6 weeks 

 
