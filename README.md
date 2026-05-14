1. Simple Graph

Graphs are consisted on nodes and edges. LangGrpah's calculations are done using graph based system. There is a state to define. Then it passes through edges to different nodes. Inside nodes, the state will be changed according to the login defined by functions. Those functions take state as the input and return updated state.

![simple graph](/images/simple_graph.png)

2. Conditional Edges

For adding conditions to the graph, we can use add_conditional_edge method.

![conditional graph](/images/conditional_graph.png)

3. Chatbot

To create simple chatbot, we can just simply maintain its short term memory using a state (include messages in a state and append the future messages to it)

![chatbot graph](/images/chatbot.png)

4. chatbot with tool call

We can bind set of tools to the llm using langchain_core module. when we invoke llm with tools, llm can decide whehter it needs to call a tool or not.

![tool call graph](/images/tool_call.png)

5. tool call agent

Here, tool response goes to chatbot and process it before final response gets prepared.

![tool call agent graph](/images/tool_call_agent.png)
