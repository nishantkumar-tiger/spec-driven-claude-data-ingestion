# spec-driven-claude-data-ingestion
AI Led Data ingestion code generation by Claude code using spec-driven phase development
Today, Data engineers hand-build every stage of this pipeline for each new vendor source. We're using Claude Code agents, working from a written spec per source, to generate the ingestion, transformation, and cataloguing code — turning a multi-week manual build into a reviewed pull request.
-Spec-driven development means: write a spec first, save it as a file, then use that file as the single source of truth for implementation. Claude reads the spec. Claude implements the spec. If the spec is wrong, you fix the spec, not the chat history.


