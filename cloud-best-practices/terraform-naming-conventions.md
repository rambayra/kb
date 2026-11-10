---
title: Terraform naming conventions (resources and data sources)
source: https://www.terraform-best-practices.com/naming
type: docs
topics: [cloud-best-practices, platform-engineering, coding]
added: 2026-11-10
status: needs-review
---

## Summary
Conventions from terraform-best-practices.com for naming Terraform resources
and data sources and ordering their arguments. The core idea: the resource type
already says *what* it is, so the name should only say *which one*. Default to
`this` when a module has a single resource of a type, and keep argument order
consistent (meta-arguments first, `tags`/`depends_on`/`lifecycle` last).

Note: the clipping only covered the "Resource and data source arguments"
section. The source page has more (e.g. variables, outputs) that isn't captured
here, hence `needs-review`.

## Key takeaways
- Don't repeat the resource type in the name, fully or partially:
  `aws_route_table.public`, not `public_route_table` or `public_aws_route_table`.
- Name a resource `this` when it's the only one of its type in the module, or
  when there's no better general name. Use descriptive names (`private`,
  `public`, `database`) when there are several of the same type. Example: the
  AWS VPC module has one `aws_nat_gateway` (`this`) but many route tables.
- Use singular nouns.
- Use `_` in Terraform identifiers but `-` in values a human will see
  (e.g. DNS names, resource names in the console).
- Put `count` / `for_each` first in the block, followed by a blank line.
- Put `tags` as the last real argument, then `depends_on`, then `lifecycle`,
  each separated by one blank line.
- For conditional `count` / `for_each`, prefer a boolean variable over
  expressions like `length(...)`.

## My take / how I'd apply it
- 

## Short quotes (optional, keep brief)
> Do not repeat resource type in resource name (not partially, nor completely)

## Related
- (no related notes yet)
