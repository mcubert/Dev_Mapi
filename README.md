MAPi Prime Template Repository

Purpose
This repository is a deployment template for MAPi Prime–governed agent ecosystems. It provides a ready‑to‑clone structure, starter configuration, and reference assets so you can spin up new MAPi instances and agents quickly, with governance discipline baked in from day one.

---------------------------------------------

Top‑Level
/MAPi_Prime
    /Versions
    /Change_Logs
    /Scenario_Library
    /Metrics_Baselines
    /Governance_Ritual_Reports
/Agents
    /_TEMPLATE_AGENT
        /Change_Logs
            change_logs.csv
        /Go_NoGo_Reports
            go_no_go_report.md
        /Manifests
            manifest.csv
        /Scenario_Results
            scenario_results.csv
        /Validation_Reports
            validation_report.md
        inbox.csv
        outbox.csv
/Config
    scope_whitelist.csv
    thresholds.csv
    orchestration_settings.csv
    roles_registry.csv
/Reference
    /Archetypes
    /Templates
    /Policy_Docs

--------------------------------

CSV Header Standards (semicolon‑delimited)

/Config/scope_whitelist.csv
type;name

/Config/thresholds.csv
metric;threshold

/Config/orchestration_settings.csv
setting;value

/Config/roles_registry.csv
role_code;agent_id

/Agents/_TEMPLATE_AGENT/Change_Logs/change_logs.csv
Change_ID;Date;Changed_By;Scope;Old_Version;New_Version;Change_Type;Affected_PG_RS;Reason;Validation_Ref;Rollback_Ref;Metrics_Before;Metrics_After;Status

/Agents/_TEMPLATE_AGENT/Scenario_Results/scenario_results.csv

Code
scenario_id;scenario_type;input;output;pass_fail;date_run;notes

/Agents/_TEMPLATE_AGENT/inbox.csv

Code
task_id;task_type;description;status;created_at

/Agents/_TEMPLATE_AGENT/outbox.csv

Code
task_id;result;notes;completed_at

/Agents/_TEMPLATE_AGENT/Metrics/metrics.csv

Code
metric_code;value;date_recorded;notes

--------------------------------------

How to Use This Template

1. Clone the Template
Use GitHub’s “Use this template” to create a new repository for your MAPi Prime instance.

2. Set MAPi Prime Version
In /MAPi_Prime/Versions/, ensure the correct MAPi manifest (e.g., MAPi_v5.4.md) is present.

Update /MAPi_Prime/Change_Logs if you make any modifications.

3. Configure Global Settings
Edit /Config/scope_whitelist.csv to define which agents/tools are in scope.

Adjust /Config/thresholds.csv for MT1–MT6/MT‑Q breach levels.

Update /Config/orchestration_settings.csv for autonomy level, polling intervals, etc.

Map governance roles to agents in /Config/roles_registry.csv.

4. Create a New Agent
Copy /Agents/_TEMPLATE_AGENT to /Agents/<Agent_ID>.

Rename files and update manifest with:

Agent name and role

PG/RS profile

Tool bindings

Metrics hooks

Inbox/outbox definitions

Add the agent to /Config/scope_whitelist.csv.

5. Validate Before Deployment
Run RS8 scenarios from /MAPi_Prime/Scenario_Library against the new agent.

Log results in /Agents/<Agent_ID>/Scenario_Results and /Validation_Reports.

Only deploy once pass criteria are met.

6. Operate & Govern
Follow Change Management (Chunk 9) for all modifications.

Record metrics in /Agents/<Agent_ID>/Metrics.

Log governance rituals in /MAPi_Prime/Governance_Ritual_Reports.

------------------------------------------------------

Governance Principles

Immutable History — Never overwrite; always version.

Scope Discipline — Agents act only within their whitelist.

Validation First — No deployment without RS8 pass.

Metrics Matter — MT1–MT6/MT‑Q are the heartbeat of governance.

Change Control — All changes logged, validated, and approved.


-------------------------------------------------------------------

References

MAPi Prime Manifest: /MAPi_Prime/Versions/MAPi_v5.4.md

PG/RS Codebook: /Reference/Policy_Docs/PG_RS_Codebook.md

Metrics Schema: /Reference/Templates/metrics_schema.csv

Change Log Schema: /Reference/Templates/change_log_schema.csv
