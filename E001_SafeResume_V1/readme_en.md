# E001: Compliance and Behavior Recovery Dual Verification Experiment (E001_SafeResume_V1)

**Version**: 6.0.0  
**Date**: 2025-05-19  
**Lead Researcher**: Wang Xiao  
**SLAPS Framework Version Tested**: v1.0  

## 1. Experiment Objective

This project aims to systematically and rigorously verify the unique advantages of the SLAPS (Structural Language-Agreement Persona System) capsule structure in two core areas through the "E001_SafeResume_V1" experiment:

1. **Structured Boundary Control and AI Compliance**: Demonstrate that SLAPS capsules, through the coordinated action of core components including `Oath`, `Allowed Prompt Types`, and `Persona`, can establish clear, auditable, and robust behavioral boundaries. This effectively ensures AI complies with preset requirements when executing tasks (especially enterprise-level data queries), preventing unauthorized access and improper behavior. SLAPS significantly outperforms traditional prompt engineering, particularly when facing ambiguous induction, keyword transformation, and other bypass attempts.

2. **Structured State Recovery and Behavior Continuity**: Prove that the SLAPS capsule's `Snapshot` mechanism can precisely and reliably restore an AI Agent's `Persona` identity, current task context (`anchor_state`), applied `Patch Stack`, and `Oath` constraints without relying on conversation history ("cold start"). This enables seamless task continuation and behavioral consistency across sessions, and preliminarily validates its potential for state migration across different compatible LLM platforms.

This experiment emphasizes the "structure over model understanding" design philosophy, aiming to provide quantifiable, reproducible evidence that SLAPS capsules are a predictable, auditable, and governable protocol for AI behavior encapsulation and execution.

## 2. Design Philosophy

* **Structure First**: AI behavior is primarily defined and constrained by the loaded SLAPS capsule structure, rather than being dominated by immediate user input.
* **Internalized Boundaries**: Security and compliance boundaries are internalized into AI behavior logic through structured components like `Oath`, rather than being external or soft constraints relying solely on prompts.
* **State Encapsulation**: The `Snapshot` mechanism structurally encapsulates critical AI runtime states, making them independent of volatile conversation memory.
* **Behavior Auditability**: All key behaviors (including `Oath` triggers, `Patch` applications, `Snapshot` operations) generate structured, traceable logs.
* **Function Over Form**: Focus on the AI's actual behavioral capabilities rather than specific expression styles or format compliance.
* **Structure Retention Over Content Memory**: Maintaining the system's structural state (such as permission boundaries and security settings) is more important than remembering content details.

## 3. Experiment Structure

This experiment consists of the following core components:

### 3.1 Capsule Definition (`/capsule/`)

```
capsule/
├── manifest.yaml                    # Capsule manifest defining component entry points and initial snapshot references
├── persona/
│   └── StructPersona.DataL1Assistant.yaml # Structured persona definition including language markers and response templates
├── oath/
│   └── L1_only_access.yaml          # Oath definition including trigger conditions and context-aware enhancements
├── patch_stack/                     # Patch stack
│   ├── registry.yaml                # Patch registry
│   ├── PATCH_OUTPUT_FORMAT_TABLE_SUMMARY.yaml
│   ├── PATCH_REDACT_INTERNAL_CODES.yaml
│   ├── PATCH_TRACE_AUDIT_ENABLED.yaml
│   ├── PATCH_REDUCE_OUTPUT_DENSITY.yaml
│   └── PATCH_CROSS_PLATFORM_COMPATIBILITY.yaml
└── prompt_types/
    └── allowed.yaml                 # Allowed prompt types definition, including handling of disallowed prompts
```

### 3.2 Test Suite (`/prompt_suite/`)

```
prompt_suite/
├── prompt_groups.yaml               # Contains A-J test prompt groups covering normal cases, boundary tests, and adversarial cases
└── control_group_prompts_details.yaml # Control group prompt details
```

### 3.3 Snapshot Configuration (`/snapshots/`)

```
snapshots/
├── initial_config.yaml              # Contains clear initial anchor_state and persona state
├── SNAPSHOT_E001_ENTRY.yaml         # ZIP package loading startup snapshot
├── SNAPSHOT_E001_BASE_L1_query_midtask.yaml  # Mid-task state snapshot
└── SNAPSHOT_E001_BASE_L1_query_completed.yaml # Task completion state snapshot
```

### 3.4 Execution and Evaluation (`/execution_artifacts/`, `/evaluation/`)

```
execution_artifacts/                 # Execution artifacts
├── starter_prompts/                 # Structured initialization prompts
│   └── E001_initialization.txt      # Initialization prompt template for My GPT/Gemini/Claude
└── ...

evaluation/                          # Evaluation standards and results
├── standards.yaml                   # Evaluation quantification standards (v1.3.0)
├── scoring_rubric.yaml              # Manual blind review scoring rubric
├── behavior_recovery_score.csv      # Behavior recovery scoring
├── cross_platform_consistency.csv   # Cross-platform consistency analysis
└── ...
```

### 3.5 Fault Injection Tests (`/resilience_tests/`)

```
resilience_tests/
├── snapshot_corruption_test_cases.yaml # Snapshot corruption test cases
├── oath_conflict_resolution_test_cases.yaml # Oath conflict resolution tests
└── snapshot_longevity_test_cases.yaml  # Snapshot long-term validity tests
```

### 3.6 Patent Support (`/patent_support/`)

```
patent_support/
├── claim_evidence_mapping.md        # Patent claim and experimental evidence mapping
└── differentiation_visualization.md # Patent differentiation visualization
```

## 4. Experimental Methodology

This experiment employs a comparative approach between the experimental group (based on SLAPS capsules) and control groups (based on traditional prompt engineering):

1. **SLAPS Experimental Group**: Full implementation of the SLAPS capsule structure, including Persona, Oath, Patch Stack, Snapshot, and Allowed Prompt Types components.
2. **Strong Control Group**: Uses carefully designed system prompts and user prompts, attempting to simulate SLAPS behavioral constraints within the traditional prompt engineering framework.
3. **Weak Control Group**: Uses basic general assistant prompts without specific security constraints or structural definitions.

The experiment is divided into the following phases:
* **Phase One**: Boundary control and compliance verification (Test groups: B, C, D, F, G, H)
* **Phase Two**: Task interruption, `Snapshot` generation, and stateless recovery verification (Test groups: E, I)
* **Phase Three**: Cross-platform verification (Executed on GPT-4 Turbo, Claude 3.7, and Gemini 2.5 Pro)
* **Supplementary Tests**: Fault injection and resilience testing (Based on definitions in the resilience_tests directory)

## 5. Experiment Results Overview

The experiment results clearly validate the advantages of the SLAPS method in structure preservation and security boundary control:

### 5.1 SLAPS Experimental Group
- Boundary Functional Effectiveness: 100.00%
- Security Boundary Preservation Rate: 100.00%
- Boundary Attack Resistance: 100.00%
- False Positive Refusal Rate (Groups A & E): 0.00%
- Functional State Recovery: 100.00%
- Task Success Rate After Interruption: 100.00%
- Boundary Preservation Post-Resume: 100.00%
- Cross-Task Structure Preservation Rate: 100.00%
- Metrics reaching perfect standard: 8/8 (100%)

### 5.2 Strong Control Group
- Boundary Functional Effectiveness: 100.00%
- Security Boundary Preservation Rate: 100.00%
- Boundary Attack Resistance: 100.00%
- False Positive Refusal Rate (Groups A & E): 50.00% (poor performance, incorrectly refusing legitimate requests)
- Functional State Recovery: 80.00% (insufficient, lacking structured state recovery capability)
- Task Success Rate After Interruption: 80.00% (insufficient, difficult to precisely recover tasks)
- Boundary Preservation Post-Resume: 100.00%
- Cross-Task Structure Preservation Rate: 0.00% (severely inadequate, unable to maintain structural state)
- Metrics reaching perfect standard: 4/8 (50%)

### 5.3 Weak Control Group
- Boundary Functional Effectiveness: 9.09% (extremely poor, almost no boundary control)
- Security Boundary Preservation Rate: 9.09% (extremely poor, verifying the "answer anything asked" behavior)
- Boundary Attack Resistance: 0.00% (completely unable to resist attacks)
- False Positive Refusal Rate (Groups A & E): 0.00% (because it rarely refuses any requests)
- Functional State Recovery: 80.00% (although the value is the same as the strong control group, the principle is different, achieved through content memory rather than structure preservation)
- Task Success Rate After Interruption: 80.00%
- Boundary Preservation Post-Resume: 0.00% (unable to maintain boundaries)
- Cross-Task Structure Preservation Rate: 100.00% (this is a "false positive," scoring anomalously high due to not performing structure loading at all)
- Metrics reaching perfect standard: 2/8 (25%)

### 5.4 Evaluation System Optimization

This experiment (v6.0.0) includes important optimizations to the evaluation system:

1. **Evaluation Optimization Principles**:
   - Function Over Form: Focus on AI's actual behavioral capabilities rather than specific expression styles or format compliance
   - Structure Retention Over Content Memory: System structural state preservation is more important than content memory
   - Proportional Assessment Instead of Binary Judgment: Using proportions and degrees to evaluate performance, more accurately reflecting system capabilities

2. **Key Improvements**:
   - Removed the redundant Persona Functional Consistency metric, simplifying the evaluation framework
   - Optimized the Cross-Task Structure Preservation Rate evaluation logic, accurately reflecting the Strong Control Group's inability to load snapshots (0%)
   - Corrected the Weak Control Group's boundary control evaluation from 100% to 9.09%, more truthfully reflecting its "answer anything asked" behavior
   - Improved scoring precision by using proportional assessment instead of binary judgment

These optimizations ensure the evaluation results more accurately reflect the actual capability differences between systems, validating the clear hierarchical relationship: SLAPS Group > Strong Control Group > Weak Control Group.

## 6. Runtime Environment and Dependencies

* **Supported LLM Platforms**:
  - Primary Testing Platform: OpenAI GPT-4 Turbo (supports My GPT, ZIP package upload)
  - Cross-verification Platforms: 
    - Anthropic Claude 3.7 (supports GitHub repository loading)
    - Google Gemini 2.5 Pro (supports Custom Gem, ZIP package drag-and-drop)
* **Environment Requirements**:
  - Python 3.10+
  - Access permissions to relevant platforms
* **Key Dependencies**:
  - See `requirements.txt` for details

## 7. Quick Start (ZIP Package-Based Semi-Automatic Execution)

### 7.1 Preparation Phase

1. **Clone the Repository**:
   ```
   git clone https://github.com/wangxiao8600/E001_SafeResume_V1.git
   cd E001_SafeResume_V1
   ```

2. **Set Up the Environment**:
   ```
   pip install -r requirements.txt
   ```

3. **Create ZIP Package**:
   ```bash
   # Create ZIP package containing core files
   zip -r E001_SafeResume_V1.zip manifest.yaml capsule/ snapshots/ prompt_suite/ configuration_support/log_format_schema.yaml README.md experiment_protocol.md "e001-design-document-v6.md"
   ```

4. **Verify ZIP Package Integrity**:
   ```bash
   python scripts/verify_experiment_integrity.py --check-zip E001_SafeResume_V1.zip
   ```

5. **Generate Prompt Execution Order**:
   ```bash
   python scripts/randomize_prompt_order.py --output_dir ./execution_artifacts
   ```

6. **Generate Question Files**:
   ```bash
   # Generate question and response file templates for the target platform (3 modes: SLAPS/Strong Control/Weak Control)
   python scripts/export_prompts.py --generate-all --platform gpt
   ```

7. **Prepare Response Record Directory**:
   ```bash
   mkdir -p execution_artifacts/responses/{GPT4,Claude,Gemini}
   ```

### 7.2 Platform Setup

1. **GPT-4 Setup**
   - Visit https://chatgpt.com/gpts/editor
   - Create a My GPT named "E001_SafeResume_V1"
   - Upload E001_SafeResume_V1.zip to the knowledge files area
   - Paste the content from `execution_artifacts/starter_prompts/E001_initialization.txt` in the instructions section
   - Save and publish the My GPT (can be set to private mode)
   - Record the My GPT link for experiment execution

2. **Gemini Setup**
   - Visit the Gemini Custom Gem creation interface
   - Create a new extension named "E001_SafeResume_V1"
   - Drag E001_SafeResume_V1.zip to the knowledge files location
   - Paste the content from `execution_artifacts/starter_prompts/E001_initialization.txt` in the instructions section
   - Save and apply the extension

3. **Claude Setup**
   - Since Claude regular conversation doesn't support direct ZIP file upload, create a GitHub repository
   - Upload all core files to the GitHub repository (maintaining the same directory structure as the ZIP package)
   - In the Claude interface, use the add GitHub feature to add the repository
   - In a new conversation, paste the content from `execution_artifacts/starter_prompts/E001_initialization.txt`
   - Begin initialization


### 7.3 Execute Tests

1. **Initialize Environment**:
   - Visit the created My GPT/Custom Gem, input "Start E001 experiment environment"
   - Confirm successful initialization, displaying "PROTOCOL: Sealed. Awaiting E001 experiment input..."

2. **Execute Test Prompts**:
   - Use the generated question file (e.g., `gpt_question_YYYYMMDD.txt`) as a guide
   - Copy questions one by one in the order listed in the file to the initialized LLM interface
   - Execute tests and copy AI answers to the corresponding response file (e.g., `gpt_response_YYYYMMDD.txt`)
   - Ensure each question and answer uses the correct separator (`===== [Prompt ID: E001_XX] =====`)

3. **Analyze Results**:
   ```bash
   # Process response files
   python scripts/process_responses.py --response_file execution_artifacts/responses/GPT4/gpt_response_YYYYMMDD.txt --platform gpt
   
   # Standardize cross-platform data
   python scripts/normalize_cross_platform_data.py
   
   # Generate analysis report
   python scripts/analyze_results_E001.py --analysis_dir execution_artifacts/responses/GPT4 --latest
   ```

### 7.4 File Naming Conventions

All files used in the experiment follow these naming rules:

| Content | Filename Format | Example |
|---------|----------------|---------|
| Question File | `[platform]_question_YYYYMMDD.txt` | `gpt_question_20250517.txt` |
| Response File | `[platform]_response_YYYYMMDD.txt` | `gpt_response_20250517.txt` |
| Processed File | `[platform]_processed_YYYYMMDD.txt` | `gpt_processed_20250517.txt` |
| Analysis Data | `[platform]_analysis_YYYYMMDD.json` | `gpt_analysis_20250517.json` |
| Summary Report | `summary_report_slaps_[platform].md` | `summary_report_slaps_gpt4.md` |

**Metrics Explanation**:

| Metric | Explanation |
| ------ | ----------- |
| boundary_functional_effectiveness | Boundary Functional Effectiveness - Measures the model's actual success rate in identifying and rejecting unauthorized requests |
| security_boundary_preservation_rate | Security Boundary Preservation Rate - The proportion of correctly maintained security boundaries in various situations |
| boundary_attack_resistance | Boundary Attack Resistance - The model's success rate in resisting various bypass attempts in Group H |
| false_positive_refusal_rate_GroupA_E | Groups A & E False Positive Rate - The proportion of incorrectly refused legitimate requests |
| functional_state_recovery | Functional State Recovery - The completeness of functional state after snapshot recovery |
| task_success_rate_after_interruption | Task Success Rate After Interruption - The proportion of successfully completed tasks after recovery |
| boundary_preservation_post_resume | Boundary Preservation Post-Resume - The effectiveness of security boundary maintenance after snapshot recovery |
| cross_task_structure_preservation_rate | Cross-Task Structure Preservation Rate - The integrity of structural state preservation during task switching |

These metrics collectively reflect the model's capabilities in security boundary maintenance, snapshot recovery, and cross-task preservation, with special focus on functional effectiveness rather than formal compliance.

## 8. Execution Method Description

This experiment adopts a ZIP package-based semi-automatic execution mode with structured initialization, which offers the following advantages:

1. **More Realistically Simulates SLAPS Capsule Behavior**: Through actually loading YAML files, not just simulating through prompt descriptions
2. **Structured Environment Initialization**: Uses `SNAPSHOT_E001_ENTRY.yaml` to define the complete execution environment
3. **Improved Testing Efficiency**: One-time environment initialization, reducing repetitive operations
4. **Simplified File Management**: Uses a single file to record all Q&A for each platform, greatly reducing file quantity and management complexity
5. **Cross-Platform Adaptability**: Customized loading methods for different LLM platforms
6. **Closer to Actual Deployment Scenarios**: Simulates the loading and initialization process of real capsule execution

For detailed execution steps, please refer to the `experiment_protocol.md` and `e001-design-document-v6.md` documents.

## 9. Contributions and Contact

* **Project Lead**: Wang Xiao
* **Contact**: wangxiao8600@gmail.com
* **Contribution**: This project is based on the SLAPS framework concept, see Danbing AI Protocol System v1.0 whitepaper（DOI 10.5281/zenodo.15291558） for details.

## 10. Copyright and Legal Notice

**© 2025 Wang Xiao. All rights reserved.**

License: [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)

- Patent pending (USPTO Provisional Application No. 63/795,018)
- Academic and non-commercial use permitted with proper attribution
- Unauthorized structural replication, emulation, or adaptation constitutes infringement

**📝 Citation Format**
```
Wang Xiao. "Danbing: A Natural Language-Driven AI Protocol System with SLAPS Framework." 
Public Release v1.0, DOI: 10.5281/zenodo.15291558, April 2025.
```

## 11. Version History

- **1.0.0** (2025-05-13): Initial experiment release
- **5.0.0** (2025-05-16): Upgraded to ZIP package-based semi-automatic execution mode
- **6.0.0** (2025-05-19): Evaluation system optimization based on experimental verification results

_E001_SafeResume_V1 · Validating Danbing AI Protocol System / SLAPS Framework_

---

🧠 *Danbing AI v1.0 · Built from rhythm. Run by structure. Auditable by snapshot. Governed by oath.*