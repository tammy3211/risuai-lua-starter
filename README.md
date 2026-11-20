# RisuAI Lua Workspace

A lightweight workspace for writing RisuAI Lua scripts with autocomplete, type hints, and diagnostics in Visual Studio Code.

## Getting started

1. Open this folder in VS Code so the workspace configuration is loaded.
2. Install the recommended **Lua** extension (`sumneko.lua`) when prompted, or find it in the Extensions panel by searching for `@recommended`.
3. Open `main.lua` and start writing your script. Use autocomplete and hover over RisuAI API functions to view their documented parameters and return types.
4. Copy your script into the appropriate Lua script or trigger in RisuAI, then test it there.

No build step or package installation is required for editing.

## What's included

```text
.
├── .vscode/
│   └── extensions.json     # Recommended Lua extension
├── .luarc.json             # Lua Language Server configuration
├── main.lua                # Starting point for your script
└── public/
    └── lua/
        ├── risuai-types.lua # RisuAI API definitions for editor assistance
        └── json.lua         # Bundled JSON library
```

The editor is configured for **Lua 5.4** and loads `public/lua` as its library directory. It also recognizes RisuAI globals such as `onInput`, `onOutput`, `onStart`, and `onButtonClick`.

## Example

Replace the placeholder in `main.lua` with your own script. For example, an input trigger can store a value in chat state:

```lua
function onInput(id)
    setState(id, "greeting", "Hello from Lua!")
end
```

Use the definitions in `public/lua/risuai-types.lua` to explore available APIs, callbacks, and async helpers.

## Development notes

- RisuAI provides the scripting runtime and its API functions. This workspace supplies editor support; run and test RisuAI-specific behavior inside RisuAI.
- `risuai-types.lua` contains type annotations and placeholder definitions for the editor. Keep it separate from the script you paste into RisuAI.
- JSON encode/decode hints are included. The type definitions describe a runtime-provided `json` global.
- If an API is missing or its signature changes, update `public/lua/risuai-types.lua` to match the RisuAI version you use.

## Credits

The bundled `public/lua/json.lua` is by rxi and includes its MIT license notice in the file.
