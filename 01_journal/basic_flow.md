AI Agent Workflow — Quick Summary
1. User / CLI

User sends a request.

Example:

“Build a project”

↓

2. Submission Queue

Request waits in line until processed.

↓

3. Submission Loop (agent_loop.py)

Main controller.

Work:

Receive request
Decide what action to take
Send to correct handler

↓

4. run_agent()

Starts the AI execution process.

↓

5. Agentic Loop (Think → Act → Repeat)

AI continuously:

Think
↓
Choose Tool
↓
Execute
↓
Read Result
↓
Think Again

(Max ~300 cycles)

↓

6. Session

Temporary workspace for current conversation.

Stores:

Current task
Current progress

↓

7. ContextManager (Memory)

Maintains:

Chat history
Previous tool results
Auto compression when memory becomes large

Purpose:

AI remembers context.

↓

8. ToolRouter (Tool Manager)

AI selects external tools.

Examples:

Documentation search
GitHub search
Sandbox/code execution
Planning tools
External servers

Purpose:

AI does real work instead of only generating text.

↓

9. Doom Loop Detector

Monitors repeated actions.

Example:

Search
Search
Search

Stops infinite loops.

↓

10. LLM Call (Brain)

Model decides:

What to do?
Use tool?
Answer directly?

↓

11. Tool Calls

If needed:

Search
Run code
Fetch data

↓

12. Approval Check

Sensitive actions require permission.

Example:

Execute code
Destructive operations

↓

13. Execute Tool

Tool runs and returns output.

↓

14. Save Result

Output stored in ContextManager.

↓

15. Repeat Until Complete

Continue loop until task finishes.

↓

Final Output

Return answer to user.

One-line memory trick
User
→ Queue
→ Controller
→ Agent
→ Think
→ Use Tools
→ Store Memory
→ Prevent Loops
→ Repeat
→ Final Answer
Easy Formula
Input → Plan → Think → Tool → Result → Memory → Repeat → Output
