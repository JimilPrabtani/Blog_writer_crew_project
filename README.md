<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Blog Writing Crew with CrewAI

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-crewai-blog-writing-crew)

**Author:** Jimil Prabtani  
**Email:** jimilprabtani0816@gmail.com

---

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_h6t9b3y7)

---

## Introducing Today's Project!

In this project, I'm going to build a multi-agent system using CrewAI to research, write and edi a blog post for me. I'm interested in this because I want to learn how I can easily deploy Multi-agent systems.

### Key tools and concepts

The key tools I used include Gemini API key, CrewAI and UV Python packages manager. Key concepts I learnt include making agents and assigning them tasks, automating simple processes like writing blog posts and Social media posts.

### Challenges and wins

This project took me approximately 2 hours to complete. The most challenging part was to engineer a good prompts for the agents to work on because with a good prompt agent cannot working properly and cannot generate desired outputs.

### Personal reflection

I did this project today to learn how to make and manage agents + tasks using CrewAI. Another skill I want to learn is how to making agent that can help me learn and build along side with me. Thank you! Have a Wonderful Day.

---

## Installing Python and CrewAI

In this step, I am setting up my environment for the project. This includes verifying Python, installing `uv`, and preparing the package manager that CrewAI uses.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_v8bn4x1w)

### Commands to install the environment

```bash
python --version
python -m pip install --upgrade pip setuptools wheel
python -m pip install uv
```

Once the repository is cloned, install the project dependencies with:

```bash
uv install
uv lock
```

### Understanding the uv package manager

I learned that uv is a Python package manager and CrewAI uses it because it is a Python-based framework and it is faster than pip.

---

## Scaffolding the CrewAI Project

In this step, I am going to set up the project locally, explore its structure, and connect the repository files with the CrewAI workflow.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_v4nt8wf6)

### Commands to clone and inspect the project

```bash
git clone https://github.com/<your-github-username>/blog_writing_crew.git
cd blog_writing_crew
```

If you want to open the project in VS Code:

```bash
code .
```

### Key project files

Two key files are `agents.yaml` and `tasks.yaml`, which define agents and the tasks each agent performs. `main.py` is the entry point that kicks off the crew, and `crew.py` wires everything together.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_w2dc5nq8)

---

## Configuring AI Agents

In this step, I'm going to replace the default agents with three custom agents and configure each of them with a role, goal, and backstory.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_j3x8n1v6)

### Commands to configure agents and model settings

Open the agent configuration file:

```bash
code src/blog_writing_crew/config/agents.yaml
```

Create or update `.env` in the project root with your Gemini credentials and model:

```env
GEMINI_API_KEY="your-gemini-api-key"
MODEL=google/gemini-2.0-flash
```

If you want to use Gemma instead, set:

```env
GEMINI_API_KEY="your-gemini-api-key"
MODEL=google/gemma-4-31B-it
```

On Windows PowerShell:

```powershell
$env:GEMINI_API_KEY = "your-gemini-api-key"
$env:MODEL = "google/gemini-2.0-flash"
```

### How agent configuration shapes AI behavior

I configured three agents: Research Analyst, Blog Writer, and Senior Content Editor. The `{topic}` variable is used because when you pass in a topic like "AI in SWE or Cybersecurity" and CrewAI automatically swaps `{topic}` for that value.

---

## Defining the Task Pipeline

In this step, I'm defining tasks for all three agents. These tasks are important because we need to assign tasks to the agents in order for them to work and give proper results.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_p3n8v5w1)

### Commands to review task definitions

Open the task configuration file:

```bash
code src/blog_writing_crew/config/tasks.yaml
```

Make sure task names and agent assignments match the entries in `agents.yaml`.

### How the tasks chain together

The tasks chain together by research, write, then edit. Only the editing task has `output_file` because after this task your final output will be generated.

---

## Connecting YAML Configuration to Python

I'm connecting two YAML files with two Python files.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_p3n8v2q6)

### Commands to inspect the crew code

Open the core crew files:

```bash
code src/blog_writing_crew/crew.py
code src/blog_writing_crew/main.py
```

Make sure the method names in `crew.py` match the YAML keys in `agents.yaml` and `tasks.yaml`.

### Why method names must match YAML keys

The method names need to match because we need to change default agents and tasks added to the YAML files in order to connect `crew.py` to both of those files.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_h8f4d6a2)

---

## Running the Blog Writing Crew

In this step, I'm going to install dependencies, watch agents work together to produce a blog post about the future of AI and LLMs, and experiment with different topics.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_p4n8v1q6)

### Commands to run the project

From the project root:

```bash
uv run blog_writing_crew
```

If you prefer the script alias:

```bash
uv run run_crew
```

### How the agents collaborated

I ran my crew and the agents collaborated with each other as defined in the `crew.py` files one after another completing tasks assigned to each agent, and to be honest it is a very efficient way to generate blog posts like this.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_h6t9b3y7)

---

## Adding a Social Media Manager Agent

In this project extension, I'm adding a Social Media manager agent to the workflow because there is no harm in generating social media posts for Twitter and Linkedin on the bases of the blog post that is generated.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_w3f8j1v6)

### Extending the crew with new agents and tasks

I added the social media manager by creating a new agent in `agents.yaml`, then assigned a task to it in `tasks.yaml`, and finally added a calling function in `crew.py` to make the agent work.

![Image](http://learn.nextwork.org/affectionate_green_mysterious_penguin/uploads/ai-crewai-blog-writing-crew_t6c1g4q8)

### Social media output

In this project extension, my social media agent generated 3-4 socail media posts based on the blog post research. The Twitter thread has 2 pieces of content and  The LinkedIn post also has 2 pieces of content.

### Experimenting with agent backstories

When I changed the backstory to more casual gen z tone and the output changed by this additional in the backstory of the agent, This showed me that we can basically make them write anything we want, we just need an idea.

---

## Contributing

If you want to contribute to this project, follow these steps:

1. Fork the repository on GitHub.
2. Clone your fork locally:

```bash
git clone https://github.com/<your-github-username>/blog_writing_crew.git
cd blog_writing_crew
```

3. Create a feature branch:

```bash
git checkout -b feature/your-feature-name
```

4. Make your changes in the code, YAML config files, or documentation.
5. Install dependencies locally and verify your changes:

```bash
uv install
uv run blog_writing_crew
```

6. Commit your changes with a clear message:

```bash
git add .
git commit -m "Add <short description of change>"
```

7. Push your branch:

```bash
git push origin feature/your-feature-name
```

8. Open a pull request on GitHub and describe your changes.

### Contribution tips

- Keep agent names and task names aligned between `src/blog_writing_crew/crew.py` and `src/blog_writing_crew/config/*.yaml`.
- Update `README.md` if you add new commands, features, or setup steps.
- Add or improve examples in `blog_outputs/` when you change the blog generation workflow.

---
