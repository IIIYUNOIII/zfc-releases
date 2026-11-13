# ZFC releases and buildless algorithm policies

This repository holds public Zero Frame Counter update metadata, binary packages (once published) and **data-only search algorithm programs**.

## File types

- [algorithm.json](algorithm.json) — legacy schema 1, for installed ZFC v0.4.17/v0.4.18 clients. Only bounded numeric tuning.
- [algorithm-v2.json](algorithm-v2.json) — schema 2, for ZFC v0.4.19+ clients. Limited arithmetic bytecode plus ARR prioritization patterns and AB representative selection.
- beta.json / stable.json — verified binary update manifests, when released separately.

## Editing algorithms without recompiling

1. Install ZFC v0.4.19 or later **once**. Earlier binaries do not contain the expression interpreter.
2. Open [algorithm-v2.json](algorithm-v2.json), edit scripts/arr_plan/ab and increase the integer revision.
3. Commit the file. With automatic algorithm checks enabled, the client downloads and validates it and loads the updated data on **next game startup**. The .geode does not need to be recompiled for an already supported script/plan edit.

## Safety and limitations

Only whitelisted arithmetic with bounded size/depth, numeric inputs and bounded ARR proposal patterns are executable. No OS/file/network access, no arbitrary native code, no Geode hooks, no game-memory access. Every final 1–12-frame/death/GOAL determination still needs real native GD simulation. Priority scripts cannot remove legal input candidates or fabricate a proof.

**Not all future changes can be buildless.** New C++ engine functions, game hooking, native collision behavior, unsupported DSL operations, or bugs in the interpreter itself require another binary build.

Reference code and Korean guidance: [ZFC v0.4.19 VM documentation](https://github.com/IIIYUNOIII/frame-window-lab/blob/ucr12-classic-v2-development/docs/ZFC-v0.4.19-BUILDLESS-ALGORITHMS-KO.md).
