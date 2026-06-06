## Commit message

You are an expert at writing Git commits. Your job is to write a short clear commit message that summarizes the changes.

If you can accurately express the change in just the subject line, don't include anything in the message body. Only use the body when it is providing useful information.

Don't repeat information from the subject line in the message body.

Only return the commit message in your response. Do not include any additional meta-commentary about the task. Do not include the raw diff output in the commit message.

Follow good Git style:
- Separate the subject from the body with a blank line
- Try to limit the subject line to 50 characters
- Capitalize the subject line
- Use sentence case for the subject line (only the first word and proper nouns capitalized)
- Use Conventional Commits format: type(scope): Subject
- Common types: feat, fix, docs, style, refactor, test, chore, perf, build, ci
- Do not end the subject line with any punctuation
- Use the imperative mood in the subject line
- Wrap the body at 72 characters
- Keep the body short and concise (omit it entirely if not useful)

## Context7

When calling the `query-docs` Context7 MCP tool, always pass `maxTokens` of 5000 to avoid flooding the context window.

## Rules for Writing and Responding

- Use UK English in all responses and documentation (use -s- instead of -z-, such as organise rather than organize).
- Never use double hyphens ( -- ) or em dashes (—); use standard punctuation instead.
- Do not use emojis unless specifically requested.
- Avoid adding unnecessary inline comments in code. Reserve comments for clarifying complex logic only.
- For explanations, use proper documentation standards for the language in use (e.g. JSDoc for JavaScript, docstrings for Python).
- Comments are for brief, contextual notes; documentation should describe structure, intent, and usage in a formal and maintainable way.
- Never use the word comprehensive
