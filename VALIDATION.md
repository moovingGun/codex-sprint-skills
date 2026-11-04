# Validation

Reviewed on 2026-11-04. These are instruction-only Skill adaptations.

## Completed checks

- Parsed every SKILL.md YAML frontmatter with Ruby's standard YAML parser.
- Checked six Skills (five adaptations, one original), directory/name equality, descriptions and per-Skill licenses.
- Compared bundled license texts byte-for-byte with the reviewed upstream license files.
- Checked per-Skill attribution for source revision and modification notices.
- Checked repository Markdown relative links.
- Reviewed all five instructions for self-contained use without mandatory other Skills,
  subagent dispatch, approval handoff loops or blanket deletion of existing code.
- Confirmed no executable scripts, hooks, MCP configurations, application code or datasets
  are bundled in the release.
- Reviewed the public file set to exclude task-specific inputs, real session history,
  credentials and local account paths.

## LITE revision (2026-11-04)

- Re-parsed all six SKILL.md frontmatters after the LITE rewrite.
- Confirmed each adaptation's ATTRIBUTION.md records the LITE modification.
- Confirmed `sprint-understanding-check/LICENSE` names the repository author, not an upstream author.

## Minimum-check revision (2026-11-04)

- Parsed all six Skill frontmatters and checked manifest/name/license consistency.
- Checked relative links and unchanged upstream license texts for five adaptations.
- Checked the README shell block with bash syntax validation and temporary fixtures:
  fresh installation includes five default Skills; existing AGENTS.md and Skill files survive.
- Reviewed the single 150-minute budget, optional understanding step, impact-based reruns,
  actual export schema, dataset version handling and session-history submission reminders.
- No timed web-service development, Docker deployment or coding-agent behavioral evaluation
  was performed as part of these packaging/documentation checks.

## Limits

These checks validate packaging and source attribution, not coding-agent performance.
The Skills have not been behaviorally evaluated on a complete timed development run.
They have not been tested in a competition environment and do not guarantee acceptance,
correct optimization results, security, or a working Docker deployment.
Test/build/Compose commands in the instructions must be checked against the actual project.
No browser, Docker image pull, package installation or target application execution is
required by the packaging checks above.

The system skill-creator quick validator was unavailable in the default Python environment
because PyYAML was not installed; frontmatter was independently parsed with Ruby YAML.
