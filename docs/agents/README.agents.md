# :robot: Custom AI Agents

This page contains the insights related to the creation, usage and evaluation of the **custom agents** defined in this repository through standard techniques. See more [here](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents).

## :bar_chart: Benchmark

This is a **small and very simple assessment** of the results obtained after running the below prompt against the following listed LLMs under these conditions:

- The prompt is the same for all the LLMs (see below).
- All the LLMs had access to the same customizations and tools (custom agent, skills, MCP servers, etc).
- The experiment was done using my **GitHub Copilot Pro license** from my **VS Code (1.108.2)** local installation.

The shorlisted LLMs are all included as part of the used Copilot license (Pro). Some are *cheaper* than others (considered *premium requests*):

- GPT-4.1 (non premium)
- GPT-5.2-Codex (premium)
- Grok Code Fast 1 (non premium)
- Raptor Mini (non premium)
- Gemini 2.5 Pro (premium)
- Gemini 3.0 Pro (premium)
- Claude Haiku 4.5 (premimu)
- Calude Sonnet 4.5 (premimu)

Other available LLMs were ruled out (i.e. Claude Opus, Gemini Flash, GPT-5.1, etc) due to various reasons (lower versions, intended for different scenarios, etc).

### The prompt

> Define the following AWS architecture following best principles and recommended practices: A serverless application needs to load a file, process it, save some metadata information in a NO-SQL storage and dump a new file for long term storage. All must be event-driven, based on the availability of the files to process. We also need some monitoring of the whole process and a way to debug it in case of issues. The serverless application needs to connect over the Internet with a third-party using some credentials that must be stored in a safe place.

### Expected output

The reference used to evaluate the output of the LLMs is defined as followed:

- **Use of D2 skill** - It is mandatory for all the LLMs to make use of the D2 skill, either partially or complete.
- **Elaboration of diagrams and images** - They must create all the requested diagrams applying the rules indicated in the skill. Additionally they must generate the required images, if possible using the provided instructions within the skill.
- **Use of MCP servers** - They should try to use the available MCP servers configured as tools within the custom agent to retrieve up-to-date information.
- **Use of other tools** - Additionally to the usage of the MCP servers, there are other tools (built-in) configured with the custom agent that should be recommended by the LLM.
- **Cost estimation** - The customization explicitily mentions the addition of a cost estimation as part of the final report.
- **Included references** - Used referneces should be added to the final report.
- **Quality of the proposed solution** - The overall quality of the generated report considering:
  - Technical quality of the dumped report (elaboration, descriptions, included content, quality of the plotted diagrams, etc).
  - Technical quality of the proposed solution (too simple, overcomplicated, well suited).

### The results

> Legend:
>
> - Overall Mark:
>   - 1 -- Very poor
>   - 2 -- Poor
>   - 3 -- Medium
>   - 4 -- Good
>   - 5 -- Very good

| Model                  | Overall Mark | Owner  | Premium Request | Type        | Use D2 Skill | Create SVG as Indicated        | Use MCP Servers | Use Other Tools | Quality | Included Cost Estimation Assessments   | Included References | Other Comments                                                                                                                                                                                                          |
| ---------------------- | ------------ | ------ | --------------- | ----------- | ------------ | ------------------------------ | --------------- | --------------- | --------------- | -------------------------------------- | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GPT-4.1                | 1            | OpenAI | No              | Specialized | Partially    | Yes, but after a second prompt | No              | Yes             | Very simple report, overly poor.         | Yes                                    | Yes                 | I needed two prompts to have a *decent* result. In a second attmept, it also dumped files that were not requested.                                                                                                      |
| GPT-5.2-Codex          | 2            | OpenAI | Yes             | Specilized  | Yes          | Yes                            | Yes             | Yes             | Good, comprehensive, good diagrams, rather complex (introduce unforeseen elements like SQS for scalability). Cost estimation a bit poor.            | Yes but poor                           | Yes                 | It had some hassles but it was able to complete with average quality.                                                                                                                                                   |
| Grok Code Fast 1       | 4            | xAI    | No              | Specialized | Yes          | Yes                            | Yes             | Yes             | Very Good, comprehensive, good diagrams, avoid overcomplication. Cost estimation is detailed enough.       | Yes                                    | Yes                 | It got stuck and had to solve some issues with the image generation but after approving continuation it completed all well. I also had to amend the report to fix the relative paths to the images that were incorrect. |
| Raptor mini (Preview)  | 1            | GitHub | No              | Specialized | Yes          | Yes but had serious troubles   | No              | Yes             | Simple report, did not embed diagrams. Cost estimation is very high level.         | Only overview but asked for refinement | Yes                 | It had troubles to perform some steps and took longer than expected. It did not follow all the instructions to create the final report.                                                                                 |
| Claude Haiku 4.5       | 4            | Claude | Yes             | Specialized | Yes          | Yes                            | No              | Yes             | Very good, very exhaustive, diagrams can be better. Cost estimation is very well elaborated.            | Yes                                    | Yes                 | It had some troubles with the D2 diagrams and the links to the images were incorrect. It also dumped additional files not requested but useful, like a ckecklist of actions and a README file.                          |
| Claude Sonnet 4.5      | 5            | Claude | Yes             | Specialized | Yes          | Yes                            | Yes             | Yes             | Outstanding, very comprehensive, diagrams are really good. Cost estimation very elaborated. Full of references.         | Yes                                    | Yes                 | Efficient, accurate, quick. Did all without errors or blockers, simply awesome :astonished:                                                                                                                             |
| Gemini 2.5 Pro         | 2            | Google | Yes             | General     | Yes          | Yes                            | No              | Yes             | Good, rather simple but detailed enough. Diagrams could be better. Bit overcomplicated (introducing additional resources). Cost estimation is high level and just a few references.          | Yes but rough.                         | Yes                 | It had some problems generating the images and got stuck and required continuation. The generated documentation seems a bit loushy.                                                                                     |
| Gemini 3 Pro (Preview) | 3            | Google | Yes             | General     | Partially    | Yes                            | No              | Yes             | Good. Simple as well but enough. Diagrams are better but they couls also be improved. Reduce complexity although still adding some unexpected resource. Cost estimation is better, more detailed. But again, poor in references.          | Yes but simple                         | Yes                 | It did not follow all the rules to create the D2 diagrams. Had some issues dumping the images and the quality of the final report looks poor.                                                                           |

### My conclusions

After running the previous benchmark, these are my thoughts and final conclusions:

- It is **understandable that LLMs like GPT-4.1 or the Gemini ones** score lower than others, since they are not fine-tuned for code assistant or technical tasks, but more on **general topics**. Said that, **Gemini 3** did a good job overall.
- **Raptor Mini is way behind** others focused on code assistance and technical matters.
- **GPT-5.2-Codex was a big deception**, since it should be comparable to others in the range of the LLMs specialized for code and technical topics. And moreover, it should also improve previous GPT versions (this is probably true, but not by far).
- **Grok was a nice surprise**. It did it overall well for a *non-premium* model.
- **Claude rules**. Both tested models, *Haiku and Sonnet*, outstood from the rest. Sonnet was simply amazing. The only thing that could be discussed is if so elaborated output is needed if not explicitily indicated as part of the prompt or the customization.
