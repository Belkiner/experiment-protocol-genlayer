# ExperimentProtocol

ExperimentProtocol is a GenLayer Intelligent Contract for locking a research method and acceptance criteria before a report is submitted, then evaluating whether the published report materially deviates from that pre-registered protocol. The review uses public evidence, independent validator evaluation, and an on-chain lifecycle from DRAFT to LOCKED to REVIEWED. It does not certify scientific truth; it records an evidence-based protocol-conformance assessment.

## Contract lifecycle and methods

See `experiment_protocol.py` for the full contract ABI. Inputs are validated on-chain; non-deterministic web/LLM review is executed inside leader/validator functions, and state is updated only after `gl.vm.run_nondet_unsafe` returns the consensus result.

## Validation before deployment

Use Python 3.12+ and the GenLayer tooling for the target network. Run:

```bash
genvm-lint check experiment_protocol.py
genvm-lint schema experiment_protocol.py
```

Then add direct tests with mocked web/LLM responses and run Studio integration tests before deploying. Python syntax checks alone do not prove runtime compatibility.
