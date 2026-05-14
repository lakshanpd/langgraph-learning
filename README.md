# LangGraph Fundamentals

## 1. Simple Graph

Graphs consist of nodes and edges. :contentReference[oaicite:0]{index=0} uses a graph-based execution system for computations and workflows.

A state must first be defined. Then, the state passes through edges to different nodes. Inside each node, the state is modified according to the logic defined by the corresponding function.

These functions:
- take the current state as input
- return the updated state

![simple graph](/images/simple_graph.png)

---

## 2. Conditional Edges

To add conditions to the graph, we can use the `add_conditional_edges` method.

This allows the graph to dynamically decide the next node based on the current state or logic.

![conditional graph](/images/conditional_graph.png)

---

## 3. Chatbot

To create a simple chatbot, we can maintain short-term memory using the graph state.

This is typically done by:
- storing messages inside the state
- appending future messages to the existing message history

![chatbot graph](/images/chatbot.png)

---

## 4. Chatbot with Tool Calls

We can bind a set of tools to the LLM using the `langchain_core` module.

When invoking the LLM with tools, the model can decide whether it needs to call a tool or directly respond to the user.

![tool call graph](/images/tool_call.png)

---

## 5. Tool Call Agent

In this architecture, the tool response is sent back to the chatbot before generating the final response.

This enables the LLM to:
- process tool outputs
- reason over external information
- generate a more accurate final response

![tool call agent graph](/images/tool_call_agent.png)

---

## 6. Using Memory Saver

By using `MemorySaver`, we do not need to manually manage previous messages.

When invoking the graph, we only need to pass:
- the current message
- the configuration object

The configuration can include a `thread_id`, which allows separate memory spaces for different chats or sessions.

---

## 7. Human in the Loop

If everything is fully automated, user control becomes limited.

To address this, we can introduce a **human-in-the-loop** mechanism.

For example:
- when a tool is about to perform an important action
- the graph can create an interrupt
- ask the user for confirmation
- continue execution based on the user’s decision

Interrupts are handled before reaching the end state of the graph using user commands.
