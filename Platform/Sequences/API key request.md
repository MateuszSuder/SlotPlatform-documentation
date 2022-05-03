# This might not happen as it requires a lot of work
## Request to obtain API key which allows to use slots
Users can request API Key which allow to use slots from platform on their own website.

```mermaid
sequenceDiagram
	User->>+Webapp: Request API key
	SSR->>+Database: Check for existing key
	alt exists
		SSR->>+User: Return key status
		SSR-->>Database: Change key status
	else
		SSR-->>Database: Add key for approval
	end
```

## Admin approves/rejects request for API key

```mermaid
sequenceDiagram
	Admin->>+SSR: Request list of requests for api key
	SSR->>+Database: Retrieve keys
	Database-->>-Admin: List keys
	Admin-->>+SSR: Approve/Reject key
	SSR-->>-Database: Change status of key
```