<objective>
Adapt the get-shit-done meta-prompting system from Claude Code to OpenCode. Create a complete, installable system for OpenCode users.

The end goal is to produce an npm package called "gsd-opencode" that developers can install to get the same powerful GSD workflow adapted for OpenCode instead of Claude Code.
</objective>

<context>
Source system: ./src/get-shit-done - A meta-prompting, context engineering and spec-driven development system for Claude Code by TÂCHES (https://github.com/glittercowboy/get-shit-done)

Target system: ./gsd-opencode - Adapted version for OpenCode

Key differences between Claude Code and OpenCode:
- Config folder: `~/.claude/` (Claude Code) → `~/.config/opencode/` or `.opencode/` (OpenCode)
- Commands folder: `commands/` (Claude Code) → `command/` (OpenCode - singular)
- Tool names: `AskUserQuestion` → `question`, `SlashCommand` → `/command` syntax
- Agent names: `general-purpose` → `general`, `Explore` stays the same
- XML tags: `<sub>something</sub>` → `*something*`

Reference files to read for translation rules:
- @./gsd-opencode/MAPPING.md - Complete tool/agent/path mappings
- @./src/get-shit-done/package.json - Source package structure
- @./src/get-shit-done/README.md - Source documentation

Project structure to create:
```
./gsd-opencode/
├── package.json
├── bin/
│   └── install.js (already exists, verify/complete)
├── command/
│   └── gsd/
│       └── [21 command files adapted from source]
└── get-shit-done/
    ├── references/
    ├── templates/
    └── workflows/
```
</context>

<requirements>
1. Examine all source files in ./src/get-shit-done to understand the complete system
2. Translate all command files from ./src/get-shit-done/commands/gsd/ to OpenCode format:
   - Read each source command file
   - Translate tool names according to MAPPING.md
   - Translate agent names according to MAPPING.md
   - Replace path references: `~/.claude/` → `~/.config/opencode/`, `./.claude/` → `.opencode/`
   - Replace `<sub>something</sub>` tags with `*something*`
   - Replace `AskUserQuestion` tool usage with `question` tool
   - Replace command invocation syntax as needed
   - Add proper OpenCode frontmatter: `name: gsd:command-name`
3. Copy and adapt all templates from ./src/get-shit-done/get-shit-done/templates/
4. Copy and adapt all workflows from ./src/get-shit-done/get-shit-done/workflows/
5. Copy and adapt all references from ./src/get-shit-done/get-shit-done/references/
6. Create package.json based on ./src/get-shit-done/package.json with:
   - name: "gsd-opencode"
   - description: Adapted for OpenCode
   - bin: "gsd-opencode": "bin/install.js"
   - files: ["bin", "command", "get-shit-done"]
   - Proper version, keywords, author attribution
7. Verify install.js is complete (already exists at ./gsd-opencode/bin/install.js)
8. Create README.md based on ./src/get-shit-done/README.md adapted for OpenCode

Important: The command files must be placed in ./gsd-opencode/command/gsd/ (NOT commands/)
</command>

<translation_rules>
Use the mappings from ./gsd-opencode/MAPPING.md:

Tool name replacements:
- `AskUserQuestion` → `question`
- `Bash` → `bash`
- `Edit` → `edit`
- `Glob` → `glob`
- `Grep` → `grep`
- `Read` → `read`
- `WebFetch` → `webfetch`
- `Write` → `write`

Agent name replacements:
- `general-purpose` → `general`
- `Explore` → `Explore` (unchanged)

Path replacements:
- `~/.claude/` → `~/.config/opencode/`
- `./.claude/` → `.opencode/`

Tag replacements:
- `<sub>something</sub>` → `*something*`

Command file frontmatter for OpenCode:
```yaml
---
name: gsd:command-name
description: Brief description
---
```

The frontmatter may also include `allowed-tools`, `agent`, `model`, etc. depending on the command.
</translation_rules>

<implementation>
Thoroughly analyze the source system and create a comprehensive adaptation:

1. First, read and understand:
   - @./src/get-shit-done/package.json
   - @./src/get-shit-done/README.md
   - @./gsd-opencode/MAPPING.md
   - @./src/get-shit-done/bin/install.js (for comparison with existing)

2. Read all command files to understand structure:
   - @./src/get-shit-done/commands/gsd/*.md (all 21 files)
   - Note patterns in allowed-tools, process steps, file references

3. Read all templates to understand their content:
   - @./src/get-shit-done/get-shit-done/templates/*.md
   - @./src/get-shit-done/get-shit-done/templates/codebase/*.md

4. Read references and workflows:
   - @./src/get-shit-done/get-shit-done/references/*.md
   - @./src/get-shit-done/get-shit-done/workflows/*.md

5. Create the adapted files:

   **package.json** (./gsd-opencode/package.json):
   - Base on source but adapt for OpenCode
   - name: "gsd-opencode"
   - description: "A meta-prompting, context engineering and spec-driven development system for OpenCode by TÂCHES."
   - files: ["bin", "command", "get-shit-done"]
   - Keep original author attribution (TÂCHES)
   - Update repository URL to point to gsd-opencode fork or note it's derived

   **Command files** (./gsd-opencode/command/gsd/*.md):
   - For each source command file, create adapted version
   - Replace tool names (AskUserQuestion → question, etc.)
   - Replace agent names (general-purpose → general)
   - Replace paths (~/.claude/ → ~/.config/opencode/, ./.claude/ → .opencode/)
   - Replace <sub>tags</sub> → *markdown emphasis*
   - Ensure proper OpenCode frontmatter with `name: gsd:command-name`
   - Translate allowed-tools lists to use OpenCode tool names
   - Keep all process logic, steps, and functionality intact

   **Template files** (./gsd-opencode/get-shit-done/templates/*.md):
   - Copy all templates
   - Replace path references (~/.claude/ → ~/.config/opencode/)
   - Replace <sub>tags</sub> → *markdown emphasis*
   - Keep template structure intact

   **Reference files** (./gsd-opencode/get-shit-done/references/*.md):
   - Copy all references
   - Replace any tool/agent mentions according to mappings
   - Replace path references
   - Replace <sub>tags</sub>

   **Workflow files** (./gsd-opencode/get-shit-done/workflows/*.md):
   - Copy all workflows
   - Replace tool/agent/path references
   - Replace <sub>tags</sub>

   **README.md** (./gsd-opencode/README.md):
   - Base on source README
   - Adapt all Claude Code references to OpenCode
   - Update installation instructions to use OpenCode paths
   - Update config folder references (~/.claude → ~/.config/opencode)
   - Change command examples to show OpenCode syntax
   - Update skip permissions mode guidance for OpenCode
   - Keep all badges, formatting, and structure
   - Maintain attribution to TÂCHES

6. Verify install.js (./gsd-opencode/bin/install.js):
   - Check if the existing file is complete
   - It should already have path replacements for OpenCode
   - Ensure it copies to ~/.config/opencode/command and .opencode/command
   - Verify it uses correct paths

Be thorough and consider multiple approaches for any edge cases. The adaptation must maintain the full functionality of GSD while being fully compatible with OpenCode.
</implementation>

<output>
Create the following files in ./gsd-opencode/:

**Configuration:**
- `package.json` - Package configuration for npm
- `README.md` - Complete documentation adapted for OpenCode

**Commands** (in ./gsd-opencode/command/gsd/):
- `add-phase.md`
- `complete-milestone.md`
- `consider-issues.md`
- `create-roadmap.md`
- `discuss-milestone.md`
- `discuss-phase.md`
- `execute-plan.md`
- `help.md`
- `insert-phase.md`
- `list-phase-assumptions.md`
- `map-codebase.md`
- `new-milestone.md`
- `new-project.md`
- `pause-work.md`
- `plan-fix.md`
- `plan-phase.md`
- `progress.md`
- `remove-phase.md`
- `research-phase.md`
- `resume-work.md`
- `verify-work.md`

**Templates** (in ./gsd-opencode/get-shit-done/templates/):
- All templates from source, adapted with path/tag replacements
- Including the codebase/ subfolder templates

**References** (in ./gsd-opencode/get-shit-done/references/):
- All references from source, adapted

**Workflows** (in ./gsd-opencode/get-shit-done/workflows/):
- All workflows from source, adapted
</output>

<verification>
Before declaring complete, verify:

1. All 21 command files are created in ./gsd-opencode/command/gsd/
2. Each command file has proper OpenCode frontmatter with `name: gsd:command-name`
3. Tool names are translated (AskUserQuestion → question, etc.)
4. Agent names are translated (general-purpose → general)
5. Path references are updated (~/.claude → ~/.config/opencode)
6. <sub>tags</sub> are replaced with *markdown emphasis*
7. package.json has correct name and files array pointing to "command" not "commands"
8. README.md is complete and adapted for OpenCode
9. install.js exists and has correct OpenCode paths
10. All templates, references, and workflows are copied and adapted

Test by checking:
- File count matches source (21 commands + templates + references + workflows)
- No references to Claude Code remain in command files
- All path replacements are correct
- The structure matches: ./gsd-opencode/{package.json,README.md,bin/,command/,get-shit-done/}
</verification>

<success_criteria>
- [ ] All source files examined and understood
- [ ] 21 command files created in ./gsd-opencode/command/gsd/
- [ ] All command files have proper OpenCode frontmatter
- [ ] All tool names translated correctly (question instead of AskUserQuestion)
- [ ] All agent names translated correctly (general instead of general-purpose)
- [ ] All path references updated for OpenCode
- [ ] All <sub>tags</sub> replaced with *markdown*
- [ ] package.json created with correct configuration
- [ ] README.md created with complete OpenCode-adapted documentation
- [ ] All templates copied and adapted
- [ ] All references copied and adapted
- [ ] All workflows copied and adapted
- [ ] Directory structure correct (command not commands)
- [ ] No Claude Code references remain in output files
- [ ] TÂCHES attribution maintained throughout
</success_criteria>
