# Sources — GitHub search queries

The routine runs each query below against `https://api.github.com/search/repositories`.

## Primary queries

| Name | Query | Window | Sort |
|---|---|---|---|
| ai-7d | `topic:ai created:>{{today-7d}}` | 7 days | stars desc |
| ai-30d | `topic:ai pushed:>{{today-30d}} stars:>500` | 30 days | stars desc |
| llm-7d | `topic:llm OR topic:large-language-models created:>{{today-7d}}` | 7 days | stars desc |
| agents-7d | `topic:agents OR topic:ai-agents created:>{{today-7d}}` | 7 days | stars desc |

## Secondary queries (dedupe against primaries)

| Name | Query | Window | Sort |
|---|---|---|---|
| mlops-7d | `topic:mlops OR topic:llmops created:>{{today-7d}}` | 7 days | stars desc |
| rag-7d | `topic:rag OR topic:retrieval-augmented-generation created:>{{today-7d}}` | 7 days | stars desc |

## Excluded topics

Drop any repo tagged with these (too generic / not AI):
- `awesome-lists`
- `tutorial`
- `course`
- `chinese` (language-specific roundups crowd out signal)

## Notes

- `{{today-7d}}` is resolved at run time to ISO-8601 date.
- GitHub API rate limit: 30 requests/min unauthenticated, 5000/hr authenticated. Use a PAT stored in the routine's environment if you run the full matrix daily.
