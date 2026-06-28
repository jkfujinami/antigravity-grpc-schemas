# 🌌 Antigravity gRPC Schemas

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Protocol Buffers](https://img.shields.io/badge/Protocol%20Buffers-v3-blue)
![Version](https://img.shields.io/badge/Antigravity-v2.1.1-brightgreen)

A comprehensive collection of gRPC and Protocol Buffer definitions for the Antigravity ecosystem. These schemas enable the development of third-party clients, SDKs, and custom integrations with Antigravity services.

**These schemas have been updated to Antigravity v2.1.1** (language server build `930583198`, 2026-06-12).

## 📦 Services Included

This repository contains Protobuf definitions for various core services:

*   **Chat Service**: Real-time AI interaction, streaming responses, and context management.
*   **Language Server (LSP)**: Code completion, symbol search, and deep source code analysis.
*   **Context & Indexing**: Codebase indexing, semantic search, and repository metadata.
*   **Browser & Tool Use**: Definitions for web browsing capabilities and agentic tool invocation.
*   **Unified State Sync**: Real-time state synchronization between clients and services.
*   **Version Control (VCS)**: Git/Fig source-control state, diffs, commits, and staging *(new in v2.1)*.
*   **Integrated Terminal**: Create, stream, and control terminal sessions *(new in v2.1)*.

## 🆕 What's New in v2.1.1

Updated from v2.0 by re-extracting the embedded `FileDescriptorProto` descriptors from the Antigravity extension bundle (v2.1.1, language server build `930583198` / 2026-06-12).

**Overall delta:** Messages +105 / ~80 changed / -1 removed · Enums +13 / ~8 changed · Services ~2 changed (additive — no RPCs removed).

**New `.proto` files**

*   `exa/vcs_pb/vcs.proto` — version-control (Git/Fig) state.
*   `exa/google/internal/cloud/code/v1internal/prediction_service.proto` — prediction service.

**New RPCs on `LanguageServerService`**

*   **Version control / Git:** `GetVersionControlState`, `WatchVersionControlState`, `GetVersionControlFileContent`, `GetCommitDetails`, `FigSync`, `FigCommit`, `FigAmend`, `FigUpload`, `GitStage`, `GitUnstage`, `GitCommit`, `GitDiscard`.
*   **Integrated terminal:** `CreateTerminal`, `StreamTerminalOutput`, `SendTerminalInput`, `CloseTerminal`, `ListTerminals`.
*   **Misc:** `ListProfiles`, `RetrieveUserQuotaSummary`, `SetupJetskiChat`, `DetectBattleModeAutoTrigger`, `EliminateBattleModeArm`, `IsProjectsEnabledInternally`.

**Other**

*   `JetskiService`: new `BattleModeAutoTrigger` RPC.
*   Removed: `exa.cortex_pb.ModelAliasResolutionPayload` (the only removal — no other breaking changes).

## 🚀 Getting Started

You can use these schemas by adding this repository as a git submodule or by copying the `.proto` files into your project.

### Example Compilation (TypeScript)

```bash
# Example of generating TypeScript code using protoc
protoc --plugin=./node_modules/.bin/protoc-gen-ts_proto \
  --ts_proto_out=./src/generated \
  --proto_path=./protos \
  ./protos/exa/chat_pb/chat.proto
```

## ⚠️ Disclaimer

These schemas have been extracted/reverse-engineered from the Antigravity communication protocols. They are provided "as-is" for educational and developmental purposes. This is an unofficial project and is not affiliated with the official Antigravity team. The protocol structure may change without prior notice.

## ⚖️ License & Attribution

This project is licensed under the MIT License.

If you use these extracted schemas to build your own clients, SDKs, or tools, **please provide proper attribution by linking back to this repository.**

A simple credit in your `README.md` is highly appreciated:
> **Acknowledgments:** gRPC/Protobuf schemas were reverse-engineered and extracted by [ふじゃ](https://github.com/jkfujinami/antigravity-grpc-schemas).