---
title: Naming conventions | Terraform Best Practices
source: https://www.terraform-best-practices.com/naming
author:
published: 2025-05-02
created: 2026-11-10
description:
tags:
  - clippings
  - iac
---
## Resource and data source arguments1. Do not repeat resource type in resource name (not partially, nor completely):

Copy

```
\`resource "aws_route_table" "public" {}\`
```

Copy

```
\`resource "aws_route_table" "public_route_table" {}\`
```

Copy

```
\`resource "aws_route_table" "public_aws_route_table" {}\`
```

1. Resource name should be named `this` if there is no more descriptive and general name available, or if the resource module creates a single resource of this type (eg, in [AWS VPC module](https://github.com/terraform-aws-modules/terraform-aws-vpc) there is a single resource of type `aws_nat_gateway` and multiple resources of type`aws_route_table`, so `aws_nat_gateway` should be named `this` and `aws_route_table` should have more descriptive names - like `private`, `public`, `database`).
2. Always use singular nouns for names.
3. Use `-` inside arguments values and in places where value will be exposed to a human (eg, inside DNS name of RDS instance).
4. Include argument `count` / `for_each` inside resource or data source block as the first argument at the top and separate by newline after it.
5. Include argument `tags,` if supported by resource, as the last real argument, following by `depends_on` and `lifecycle`, if necessary. All of these should be separated by a single empty line.
6. When using conditions in an argument`count` / `for_each` prefer boolean values instead of using `length` or other expressions.