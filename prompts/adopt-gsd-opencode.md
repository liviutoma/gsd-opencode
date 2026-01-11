# /create-prompt @./prompts/adopt-gsd-opencode.md

Take ./src/get-shit-done system of metaprompts for Claude Code and build similar system for opencode. The auditory is any application developer.

There are several complications.

1. The main goal is ability to run the get-shit-done propmpts as commands in opencode. All the tools, agents, names related to Claude Code should be translated to similar tools, agents, names for OpenCode.
2. Examine opencode documentation https://opencode.ai/docs.
3. The config folder for opencode is ~/.config/opencode OR .opencode/ (not ~/.claude).
4. Claude Code supports "/gsd:subcommand" syntax for the command. Add "name: gsd:<name-of-command>" to the header of every command
5. In ./src/get-shit-done the custom commands are located in the ./src/get-shit-done/commands. It is a Cloud Code notation. In OpenCode the same commands must be put into ./gsd-opencode/command folder. Important: "command" instead of "commands"
6. Just as files defined in ./src/get-shit-done/package.json you should create simialar ./gsd-opencode/package.json with the same  files from ./gsd-opencode folder.
7. Generate a ./gsd-opencode/bin/install.js script is to install the prompt and reference files to the opencode config folder, similar to ./src/get-shit-done/bin/install.js. The script should put ./gsd-opencode/command to ~/.config/opencode/command OR .opencode/command and ./gsd-opencode/get-shit-done to ~/.config/opencode/get-shit-done OR .opencode/get-shit-done.
8. Replace Claude Code tools with similar opencode tools. 
9. Replace Claude Code agent names with similar opencode agents names.
10. The author of the prompts is TACHES (https://github.com/glittercowboy/get-shit-done).
11. The name of the current project is "gds-opencode".
12. When original prompt uses "<sub>something</sub>" tegs - replace them with one star '*': *something* in the OpenCode adopted version
13. Generate README.md file with full information on how to install the system and how to use it using ./src/get-shit-done/README.md as source and example.
