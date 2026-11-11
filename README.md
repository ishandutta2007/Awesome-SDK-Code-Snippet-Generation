# Awesome-SDK-Code-Snippet-Generation

# Awesome SDK & Code Snippet Generation

> A curated list of top SDK and Code Snippet Generation platforms — both SaaS/Hosted commercial solutions and open-source alternatives for turning API specifications into typed client libraries, documentation examples, and developer tooling.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Speakeasy](#speakeasy)
  - [Fern](#fern)
  - [APIMatic](#apimatic)
  - [liblab](#liblab)
  - [Postman Code Examples](#postman-code-examples)
- [Open-Source Software](#-open-source-software)
  - [OpenAPI Generator](#openapi-generator)
  - [Swagger Codegen](#swagger-codegen)
  - [Kiota](#kiota)
  - [Redocly CLI](#redocly-cli)
  - [Snippettoni](#snippettoni)
  - [TypeSpec](#typespec)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted SDK and Code Snippet Generation platforms. These are not fully open-source (though some have open-source generators) and are included as reference points for feature comparison.

### Speakeasy
**Type:** Enterprise SDK generation with Terraform and MCP support
Speakeasy is one of the most established commercial SDK generators, with years of production SDKs at companies like Vercel. On 17 September 2026, Speakeasy released its generators under **AGPL-3.0** in the `openapi-generation` repository, covering SDKs, a CLI generator, and an **MCP server generator** [citation:2]. The repository lists TypeScript, Python, Go, Java, C#, PHP, Ruby, and Unity, plus **Terraform providers**, CLI applications, MCP servers, and Postman collections [citation:2]. The company's positioning has moved toward an AI control plane. **Important licensing note:** AGPL-3.0 has real obligations if you modify the generator and offer it as a network service; the commercial licensing route remains available [citation:2].
**Best for:** Teams needing Terraform providers alongside SDKs, or those wanting a generator they can run and read under an open license.

### Fern
**Type:** Docs and SDK platform with broad spec support (Postman)
Fern is a docs and SDK platform acquired by Postman in January 2026, with the product and brand unchanged [citation:2]. It generates SDKs in TypeScript, Python, Java, Go, Ruby, PHP, C#, Swift, and Rust, with Kotlin in progress. **Inputs include OpenAPI, AsyncAPI, gRPC (Protobuf), and OpenRPC** — broader than most competitors [citation:2]. The generators are **Apache-2.0**, making them genuinely permissive. The free SDK plan covers Python and TypeScript up to 200 endpoints; languages beyond those require an annual, per-SDK Enterprise contract [citation:2].
**Best for:** Teams with gRPC or JSON-RPC APIs, Postman customers, or anyone wanting to read the generator source under a permissive license.

### APIMatic
**Type:** Developer experience platform for SDKs and docs
APIMatic provides an intuitive, user-friendly interface for generating SDKs and API documentation across multiple languages. It offers cross-platform SDK generation, consistent documentation, and integration capabilities, though it can be expensive for smaller businesses and has some customization limitations [citation:8].
**Best for:** Organizations wanting a straightforward platform for SDK and documentation generation with a lower learning curve.

### liblab
**Type:** SDK generation platform with CI/CD integration
liblab helps companies create developer-friendly SDKs for their APIs in multiple languages, automating generation, maintenance, and optimization. It is backed by $50 million in funding and targets fintech, telecommunications, and other industries with robust API ecosystems [citation:8]. It offers API simplification, developer-friendly tooling, and scalability, though pricing may be a barrier for small projects [citation:8].
**Best for:** Companies wanting automated SDK generation integrated into their CI/CD pipelines with a focus on developer experience.

### Postman Code Examples
**Type:** Snippet generation within Postman platform
Postman provides built-in code snippet generation for API requests, allowing developers to copy requests as code in multiple languages (cURL, Node.js, Python, etc.) directly from the Postman interface. This is a lightweight snippet generation feature within the broader Postman API platform rather than a full SDK generator.

---

## 🟩 Open-Source Software

Self-hosted, community-driven SDK and Code Snippet Generation tools. The open-source ecosystem spans **mature multi-language generators**, **Microsoft-backed clients**, **API description languages**, and **specialized snippet enrichment libraries**.

### OpenAPI Generator
**Stack:** Java / Mustache templates | **License:** Apache-2.0
OpenAPI Generator is the community fork of Swagger Codegen, created in 2018 by 40+ top contributors who wanted faster releases and better direction [citation:3]. It offers **more than 50 client generators and 40+ server-stub generators**, driven by a template engine you can override [citation:1]. It reads OpenAPI 2.0 and 3.0 fully, with 3.1 support in beta and improving each release. It emits server stubs and HTML/Markdown docs alongside clients, so a spec-first team gets backend, clients, and docs from one run [citation:1]. Per-generator options are granular down to model name prefixes and nullable handling. **Nothing is uploaded** and no account is needed; the spec stays in your repository [citation:1]. Releases are frequent (v7.25.0 in August 2026) [citation:3].
**Best for:** Teams wanting the broadest language coverage, server stubs, and a drop-in migration path from Swagger Codegen, with full control over the generation pipeline.

### Swagger Codegen
**Stack:** Java / Mustache templates | **License:** Apache-2.0
Swagger Codegen is where OpenAPI code generation started, with nearly 18,000 GitHub stars and v3.0.82 released in August 2026 [citation:3]. It produces client SDKs in 40+ languages and server stubs in 20+, from OpenAPI 2.0 and 3.0 definitions. **Critical limitations:** It maintains two parallel lines (2.x for Swagger 2.0, 3.x for OpenAPI 3.0), **neither of which covers OpenAPI 3.1** — the request has been open since August 2023 [citation:3]. Upgrading to 3.x can also lose languages (Rust, Elixir, Haskell, Objective-C are 2.x-only). Community momentum has moved to OpenAPI Generator, with around 3,000 open issues and some features open since 2017 [citation:3].
**Best for:** Existing users with Swagger 2.0 specs that will not change, accepting irregular releases and the lack of 3.1 support.

### Kiota
**Stack:** C# / .NET toolchain | **License:** MIT
Kiota is Microsoft's open-source client generator, a CLI that turns OpenAPI 3.x into a strongly typed client with IDE autocompletion. Stable languages are **C#, Go, Java, PHP, and Python**, with Dart, Ruby, and TypeScript in preview [citation:1]. A standout feature is **selective generation** — you can generate a client for only the endpoints you need, keeping output small for large APIs like Microsoft Graph. The raw HTTP request is exposed underneath when you need to drop down a level. **Limitations:** Setup leans on the .NET toolchain even when the target language is not C#, and it produces clients only (no server stubs or docs) [citation:1].
**Best for:** .NET shops and teams consuming large APIs where selective endpoint generation matters, or anyone wanting a Microsoft-maintained MIT-licensed client generator.

### Redocly CLI
**Stack:** TypeScript / Node.js | **License:** MIT
Redocly CLI's **`generate-client`** command (powered by `@redocly/client-generator`) turns one OpenAPI description into typed SDKs in **TypeScript, Python, Go, and PHP**, plus validation schemas, TanStack Query/SWR hooks, test mocks, a ready-to-run CLI, and reference docs [citation:10]. The generated SDKs include auth from `securitySchemes`, pagination iterators, opt-in abort-aware retries with exponential backoff, **typed Server-Sent Events**, composable middleware, and strict argument validation that fails before the request leaves the process [citation:10]. It reads OpenAPI 3.0, 3.1, 3.2, and Swagger 2.0. Both the command and package are MIT, and everything generated is yours outright. **Note:** It covers four languages, fewer than OpenAPI Generator or Speakeasy [citation:10].
**Best for:** Teams wanting modern, production-grade TypeScript/Python/Go/PHP clients with built-in pagination, retries, and SSE support under a permissive license.

### Snippettoni
**Stack:** Python | **License:** Apache-2.0
Snippettoni is a Python library that generates the **`x-codeSamples`** extension for OpenAPI specifications, supporting multiple programming languages with custom templates [citation:4]. It enriches an OpenAPI spec with code examples that appear in documentation tools, rather than generating full SDKs. Install via `pip install snippettoni`, then run `snippettoni enriched_openapi_spec.yaml openapi_spec.yaml` to add code samples. Options include `--lang` for specific languages, `--template` for custom per-language templates, and `--base-url` for example URLs [citation:4].
**Best for:** Teams wanting to automatically enrich their OpenAPI specs with multi-language code examples for documentation, without a full SDK generation pipeline.

### TypeSpec
**Stack:** TypeScript-like language | **License:** Open Source (Microsoft)
TypeSpec is Microsoft's API description language that compiles to OpenAPI (and other formats), addressing the pain of writing OpenAPI YAML by hand [citation:5]. Azure's entire API surface is defined in TypeSpec. Advantages include type-checked definitions, reusable models with TypeScript-style generics, a single source that generates OpenAPI, JSON Schema, and potentially gRPC proto files, and better diff/merge behavior than YAML [citation:5]. **Trade-off:** It is an API description language rather than a direct SDK generator, and the learning curve is steeper than writing OpenAPI directly. It is most useful for large API teams managing complex surfaces [citation:5].
**Best for:** Large API teams wanting a type-safe, programmatic way to define APIs that then feeds into SDK generation pipelines, particularly in the Azure/Microsoft ecosystem.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Languages | Server Stubs | Self-Hosted | Best For |
|----------|---------|-------|-----------|--------------|-------------|----------|
| **Speakeasy** | AGPL-3.0 | Cloud/CLI | 8+ (incl. Terraform) | ❌ | ✅ (AGPL) | Terraform + SDKs |
| **Fern** | Apache-2.0 | Cloud/CLI | 9+ | ❌ | ✅ (Apache) | gRPC/OpenRPC + Postman |
| **APIMatic** | Proprietary | Cloud | Multi-language | (Check) | ❌ | User-friendly SDK/docs |
| **liblab** | Proprietary | Cloud | Multi-language | ❌ | ❌ | CI/CD SDK automation |
| **OpenAPI Generator** | Apache-2.0 | Java/CLI | 50+ clients | ✅ 40+ stubs | ✅ | Broadest coverage + stubs |
| **Swagger Codegen** | Apache-2.0 | Java/CLI | 40+ | ✅ 20+ | ✅ | Legacy Swagger 2.0 |
| **Kiota** | MIT | .NET CLI | 5 stable + 3 preview | ❌ | ✅ | Selective endpoint clients |
| **Redocly CLI** | MIT | TypeScript | 4 | ❌ | ✅ | Modern TS/Py/Go/PHP clients |
| **Snippettoni** | Apache-2.0 | Python | (Code samples) | ❌ | ✅ | OpenAPI x-codeSamples |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source SDK or Code Snippet Generation tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source (or clearly note the license if source-available but not OSI-approved, as with Speakeasy's AGPL). Note that the ecosystem **splits** between **commercial platforms** (Speakeasy, Fern, APIMatic, liblab) that handle hosting, CI, and publishing, and **open-source generators** (OpenAPI Generator, Kiota, Redocly CLI) that leave those responsibilities to you. **OpenAPI Generator** remains the broadest open-source option with 50+ client generators and server stubs [citation:1], while **Redocly CLI** offers the most modern generated client behavior (pagination, retries, SSE) under MIT [citation:10]. **Speakeasy** and **Fern** are notable for having open-sourced their generators under AGPL and Apache-2.0 respectively, giving teams the option to run them without vendor lock-in [citation:2]. **Stainless**, historically a major commercial player, announced its wind-down in May 2026 and is not included as a current option [citation:2][citation:6].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
