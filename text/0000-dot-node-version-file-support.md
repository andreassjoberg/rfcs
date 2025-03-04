- Feature Name: dot_node_version_file_support
- Start Date: 2025-03-04
- RFC PR: (leave this empty)
- Volta Issue: (leave this empty)

# Summary
[summary]: #summary

Introduce support for a `.node-version` file, enabling it as a fallback source for determining project-specific Node versions. If node version is not specified in `package.json`, fallback to `.node-version` before using global defaults.

# Motivation
[motivation]: #motivation

The aim is to align Volta with other popular Node version managers like fnm, which support `.node-version`. This enhances flexibility and user experience by allowing developers to specify their preferred Node versions in a widely recognized format.

# Pedagogy
[pedagogy]: #pedagogy

Existing node developers are likely already familiar with other versioning methods like `.nvmrc`. Introducing support for `.node-version` aligns Volta with other node version managers.

# Details
[details]: #details

## Inheritance from current solution

The new feature will follow the same logic currently applied when reading a node version from `package.json`. This ensures consistency across different configuration files.

## Standardized Approach

This implementation should mirror the behavior of other Node version managers, ensuring Volta remains competitive and user-friendly.

## Fallback Hierarchy

Prioritize `.node-version` as fallback for determining Node versions.
If volta is not defined in `package.json`, check `.node-version` before proceeding with global defaults.
Continue with existing behavior if neither file specifies a version.

## Backward Compatibility

This feature does not disrupt current functionality and can be released immediately without breaking changes.

## Implementation Considerations

Ensure the implementation respects the same environment inheritance as today’s solution when reading versions from `package.json`.
Maintain consistent behavior across different scenarios, ensuring that if no specific version is found in either `package.json` or `.node-version`, Volta defaults to its standard global setting.

No new commands are required; this feature should integrate seamlessly with existing Volta commands.

## Testing Strategy

Develop comprehensive tests that cover various scenarios, including:

- Presence and absence of `.node-version`.
- Conflicting versions between `.node-version` and `package.json`.
- Interaction with global Node version settings.

# Critique
[critique]: #critique

By supporting .node-version, Volta will provide users with more flexibility in how they manage their Node environments, while maintaining its commitment to backward compatibility. This RFC invites feedback on the proposed implementation and any potential edge cases that might arise.

# Unresolved questions
[unresolved]: #unresolved-questions
