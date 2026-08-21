# Security

Report vulnerabilities privately through GitHub Security Advisories. Do not include live credentials or business data.

The verifier is offline and proof-only. It never executes actions, grants authority, signs receipts, accesses the network, or reads raw business bodies. Inline MCP tools have no filesystem parameters. File tools constrain all paths to a real workspace root, reject absolute paths, traversal and symlinks, cap evidence at 256 KiB, write only to an explicit artifact directory, publish atomically and verify by read-back. Secret-shaped and body-shaped fields are rejected recursively.

Trust boundary: hashes are opaque claims unless independently anchored. A `verified` report proves consistency of the supplied envelopes, not authenticity, completeness, non-omission, authorization correctness or real-world effect occurrence.
