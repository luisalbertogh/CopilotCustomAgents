# :robot: Custom AI Agents

This page contains the insights related to the creation, usage and evaluation of the **custom agents** defined in this repository through standard techniques. See more [here](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents).

## :bar_chart: Benchmark

### The prompt

> Define the following AWS architecture following best principles and recommended practices: A serverless application needs to load a file, process it, save some metadata information in a NO-SQL storage and dump a new file for long term storage. All must be event-driven, based on the availability of the files to process. We also need some monitoring of the whole process and a way to debug it in case of issues. The serverless application needs to connect over the Internet with a third-party using some credentials that must be stored in a safe place.

### Expected output

### The results

| Model | Overall Mark | Owner | Premium Request | Type | Use D2 Skill | Create SVG as Indicated | Use MCP Servers | Use Other Tools | Overall Quality | Included Cost Estimation Assessments | Included References | Other Comments |
|-------|--------|--------|--------|--------------|---------------|-------------------------|-----------------|-----------------|-----------------|-----------------------------|---------------------|-------------|
| GPT-4.1 | - | OpenAI | No | Specialized | Partially | Yes, but after a second prompt | No | Yes | Good | Yes | Yes | I needed two prompts to have a *decent* result. In a second attmept, it also dumped files that were not requested. |
| GPT-5.2-Codex | - | OpenAI | Yes | Specilized | Yes | Yes | Yes | Yes | Good | Yes but poor | Yes | It had some hassles but it was able to complete with average quality. |
| Grok Code Fast 1 | - | xAI | No | Specialized | Yes | Yes | Yes | Yes | Very Good | Yes | Yes | It got stuck and had to solve some issues with the image generation but after approving continuation it completed all well. I also had to amend the report to fix the relative paths to the images that were incorrect. |
| Raptor mini (Preview) | - | GitHub | No | Specialized | Yes | Yes but had serious troubles | No | Yes | Medimum | Only overview but asked for refinement | Yes | It had troubles to perform some steps and took longer than expected. It did not follow all the instructions to create the final report. |
| Claude Haiku 4.5 | - | Claude | Yes | Specialized | Yes | Yes | No | Yes | Good | Yes | Yes | It had some troubles with the D2 diagrams and the links to the images were incorrect. It also dumped additional files not requested but useful, like a ckecklist of actions and a README file. |
| Claude Sonnet 4.5 | - | Claude | Yes | Specialized | Yes | Yes | Yes | Yes | Awesome | Yes | Yes | Efficient, accurate, quick. Did all without errors or blockers, simply awesome :astonished: |
| Gemini 2.5 Pro | - | Google | Yes | General | Yes | Yes | No | Yes | Medium | Yes but rough. | Yes | It had some problems generating the images and got stuck and required continuation. The generated documentation seems a bit loushy. |
| Gemini 3 Pro (Preview) | - | Google | Yes | General | Partially | Yes | No | Yes | Medium | Yes but simple | Yes | It did not follow all the rules to create the D2 diagrams. Had some issues dumping the images and the quality of the final report looks poor. |
