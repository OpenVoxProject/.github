# Vox Pupuli and OpenVox AI Usage Policy

This document tries to summarize the AI Usage Policy within Vox Pupuli and the OpenVox Project, and some of the rationale behind it.
AI is a tool which, if used correctly, can benefit users and developers significantly.
However, just like any other tool it may be misused and may land us on [AI Darwin Awards](https://aidarwinawards.org/).

The current policy is as follows:

The use of AI tools for code contributions is allowed under strict guidelines.

- **Accountability**: You **MUST** take full responsibility for your contribution.
  - By contributing to any Vox Pupuli project, you are personally vouching for the quality, license compliance, and utility of your submission and you are personally accountable for meeting our standards.
  - You **MUST** understand every part of your submission and be able to participate meaningfully in discussions during the review process.
  - If the first human readers of your code are Vox Pupuli reviewers, then you **WILL BE** permanently prohibited from contributing to Vox Pupuli projects.
  - An AI **MUST NOT** add `Signed-off-by` tags as ***only humans can legally certify the Developer Certificate of Origin (DCO)***.
  - Fully autonomous AI agents are not allowed *full stop*. There **MUST** be a human involved and accountable.

- **Transparency**: You **MUST** disclose the use of AI tools when ***any significant part*** of the contribution is created by AI, whether or not you have since modified it.
  - For example, routine use of assistive tools for correcting grammar and spelling does not need to be disclosed, but "Rewrite with Copilot" does.
  - Each git commit message should have an attribution trailer according to the kind of augmentation used. The same attribution trailer should be duplicated in the pull request description.
    - **`Co-authored-by: Claude <noreply@anthropic.com>`** (preferred)
    - `Generated-by: chatgpt-4o`
    - `Assisted-by: AGENT_NAME:MODEL_VERSION [TOOL1] [TOOL2]`
    - `Assisted-by: Grok AI`
  - For non git-tracked contributions, the disclosure should be made in a reasonable place, such as the footer of a document.

- **Licensing and Legal**: All contributions must comply with the project's own licensing requirements. In general, this means Apache 2 or GPL, but individual projects may have different licenses and you should be aware of them.
  - If your AI tool of choice has an open source license compliant mode, then ***please use it***.
  - Prefer using AI tools with open source license compliant modes when possible.

- **Prefer collaboration over reinventing**: AI tools make it shockingly easy to just create something net-new by simply asking for it. Unfortunately, this taken to the extreme leads to a sprawling ecosystem in which we don't have any tools that work well, but we do have five mediocre tools for every need, each subtly different and each broken in slightly different ways. Unless there is a pressing need for a different approach, then we should prefer to use our new AI prompt skills to collaborate on existing projects rather than inventing new wheels.


- **Ethics**: While this is not something we can police, please be aware of the environmental and ethical costs of AI usage and default to using your human brain as much as possible. If you don't need AI to answer a question or generate content, then *please don't.*


This policy is in immediate effect.


> Inspiration borrowed from:
> - https://docs.fedoraproject.org/en-US/council/policy/ai-contribution-policy/
> - https://kernel.org/doc/html//next/process/coding-assistants.html
> - https://openinfra.org/legal/ai-policy
> - https://github.com/PowerDNS/pdns/pull/15613
> - https://theshamblog.com/an-ai-agent-published-a-hit-piece-on-me/
