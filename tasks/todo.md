# Task Plan — P1 Features: --dry-run, make setup, Project Archetypes

> Updated: 2026-02-13
> Branch: `feat/p1-features`
> Status: Complete
> Issues: #8, #9, #10

## Objective

Implement the three P1-high features: `--dry-run` preview mode, `make setup` bootstrap target, and project archetypes (CLI, API, library).

## Plan

### Phase 1: `--dry-run` flag (#10)

- [x] 1. Add `DRY_RUN=false` global
- [x] 2. Add `--dry-run` to `parse_flags()` and `show_help()`
- [x] 3. Create `dry_run_report()` — prints file tree of what would be created based on choices
- [x] 4. In `main()`, after all `step_*` prompts but before `apply_templates`: if `DRY_RUN`, call `dry_run_report` and exit
- [x] 5. Add test: `./scaffold --non-interactive --dry-run` produces no files, exits 0
- [x] 6. Update header comment with new flag

### Phase 2: `make setup` target (#9)

- [x] 7. Add per-language `SETUP_CMD` variables to Makefile
- [x] 8. Add `setup` target: run `SETUP_CMD`, `pre-commit install` if config exists
- [x] 9. Add `setup` to `.PHONY` list and `help` target
- [x] 10. Update scaffold's `show_summary()` to mention `make setup`
- [x] 11. Add test: assert Makefile contains `setup` target
- [x] 12. Update README "Makefile" section

### Phase 3: Project Archetypes (#8)

- [x] 13. Add `ARCHETYPE="none"` global
- [x] 14. Create `step_archetype()` with options: cli, api, library, none
- [x] 15. Create `apply_archetype()` with 4 languages × 3 archetypes + default
- [x] 16. Wire `step_archetype()` into `main()` after `step_language()`
- [x] 17. Add `force_archetype()` helper in tests
- [x] 18. Add tests: Python×API, TypeScript×CLI, Go×library, Rust×library
- [x] 19. Update README with archetype section
- [x] 20. Update show_help to mention archetypes

### Phase 4: Final Polish

- [x] 21. Run full test suite — 614/614 passing
- [x] 22. Update README counts and tests.md
- [x] 23. Commit, push, PR
