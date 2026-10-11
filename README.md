# CodeNinja

CodeNinja is a CrewAI-based multi-agent engineering system that turns product requirements into working software. The crew includes an engineering lead, backend engineer, frontend engineer, and test engineer that collaborate to design, implement, and validate a solution.

This project is built for Python 3.13 and uses CrewAI with MCP tooling for project work.

## What it does

The default workflow takes a requirement brief and generates a complete solution flow for a trading simulation platform, including:

- account creation
- deposits and withdrawals
- share purchases and sales
- portfolio value tracking
- profit/loss calculations
- transaction history
- validation rules for safe financial operations

## Requirements

- Python 3.13.x
- A working virtual environment
- An OpenAI API key for the CrewAI LLM calls

## Setup

From the project root:

```bash
python3.13 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m pip install -e .
```

Create a `.env` file in the project root with your API key:

```env
OPENAI_API_KEY=your_key_here
```

## Running the project

You can run the project with the CrewAI CLI:

```bash
crewai run
```

You can also run the default crew flow directly:

```bash
python -m code_ninja.main
```

Or, if the package is installed in editable mode:

```bash
code_ninja
```

## Available commands

The project exposes a few helper entry points via `pyproject.toml`:

```bash
code_ninja
run_crew
train
replay
test
run_with_trigger
```

Examples:

```bash
python -m code_ninja.main
```

```bash
train 3 output.json
```

```bash
replay <task_id>
```

## Project structure

```text
.
├── src/
│   └── code_ninja/
│       ├── crew.py
│       ├── main.py
│       ├── patch.py
│       └── tools/
├── requirements.txt
├── pyproject.toml
├── .env
├── README.md
└── knowledge/
```

## Customization

You can adapt the project by editing:

- `src/code_ninja/crew.py` to change agents and tasks
- `src/code_ninja/main.py` to adjust the default project requirements and entry behavior
- `src/code_ninja/tools/` to add custom tools
- `.env` for your environment variables

## Troubleshooting

If installation fails during dependency resolution, verify:

- Python is 3.13.x
- the virtual environment is active
- the project dependencies are installed from `requirements.txt`
- `OPENAI_API_KEY` is set before running the crew

## Notes

This project uses CrewAI and MCP integrations to coordinate specialized agents for implementation, testing, and frontend/backend work. It is intended as an agentic engineering starter for building software from natural-language requirements.
