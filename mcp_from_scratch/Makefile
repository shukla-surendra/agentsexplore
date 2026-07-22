PYTHON ?= python3

.PHONY: jsonrpc-demo client-smoke-test demo demo-quiet compare clean

jsonrpc-demo:
	$(PYTHON) jsonrpc.py

client-smoke-test:
	$(PYTHON) mcp_client.py

demo:
	$(PYTHON) demo.py

demo-quiet:
	$(PYTHON) demo.py --quiet

compare:
	diff -u ../tasks_mcp_server.py mcp_server.py || true

clean:
	rm -f tasks.json
