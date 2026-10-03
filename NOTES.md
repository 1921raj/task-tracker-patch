# Patch notes

## Changes

- Corrected the task-search predicates in the Spring repository, H2 SQL reference, and Oracle package. Explicit grouping ensures archived tasks stay excluded and the optional status filter applies to matches in either the title or description.
- Replaced in-memory slicing with Spring Data database pagination and a matching count query. The API rejects invalid page values, page sizes over 100, and unknown statuses, and no longer adds an artificial delay to requests.
- The frontend now aborts superseded fetches so a slow response cannot replace newer search results. Changing the search or status filter returns the view to page 1.

## Scope and remaining risk

I left write operations, authentication, and other future-risk areas untouched to keep this patch focused on the existing read-only search experience. Substring matching can still become slow as the task table grows; the schema currently has no search indexes.

## Tools and verification

I used GitHub Copilot to inspect the React, Spring, and SQL paths, then reviewed the patch. `npm run build` succeeded. I ran both local servers and checked search filters, database pagination, the Vite API proxy, and 400 responses for invalid parameters.

Handwritten explanation photos are not included. Add your own handwritten notes under `handwritten/` before submission.
