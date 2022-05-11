## TPM DevID Provisioning

This repository contains a set of helper scripts to demostrate how to provision DevID certificates using [HPE's DevID Provisioning Tool](https://github.com/HewlettPackard/devid-provisioning-tool).
(Tested on Linux)

### Using software TPM (swtpm) to provision DevID certificates

1. Clone and build the provisioning tool: `make build`.
2. Create and setup certificates: `make setup-provisioning`.
3. Clone and run swtpm: `make run-swtpm`. Swtm will keep running until killed. _(swtpm listens on /tmp/swtpm.sock by default)_
4. Run the provisioning server: `make provisioning-server`. The server will keep running until killed.
5. Run the provisioning agent: `make provisioning-agent`.

The DevID certificates will be in `out/`, unless a different `out_dir` is set in [`agent.conf`](conf/agent/agent.conf).

### Using hardware TPM to provision DevID certificates

1. Clone and build the provisioning tool: `make build`.
2. Create and setup certificates: `make setup-provisioning`.
3. Edit [server.conf](conf/server/server.conf) and place the manufacturer CA certs chain in the section `endorsement_bundle_paths`.
4. Edit [agent.conf](conf/agent/agent.conf) and comment `tpm_path` or set it to your hardware tpm file path.
5. Run the provisioning server: `make provisioning-server`.
6. Run the provisioning agent: `make provisioning-agent`.

