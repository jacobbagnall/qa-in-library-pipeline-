# Library Data Pipeline

![Teaching](https://img.shields.io/badge/module-DE5M5-blue)
![Python Version](https://img.shields.io/badge/python-3.9--3.12-blue.svg)

![Open Issues](https://img.shields.io/github/issues/jacobbagnall/qa-in-library-pipeline-)
![Open PRs](https://img.shields.io/github/issues-pr/jacobbagnall/qa-in-library-pipeline-)
![Last Commit](https://img.shields.io/github/last-commit/jacobbagnall/qa-in-library-pipeline-)
![CI Pipeline Badge](https://github.com/jacobbagnall/qa-in-library-pipeline-/actions/workflows/ci.yml/badge.svg)


## Project Overview
flowchart TD
  CSV[CSV source data] --> |Data validation / ingestion fields| CSVBronze[CSV Bronze layer]
  CSVBronze --> |Standardising e.g. formats, units, naming conventions, data types etc.| CSVSilver[CSV Silver layer]
  CSVBronze --> |Failures on standardising data| CSVQuar[Quarantine]
  CSVSilver --> |Access controls, reports, filtering sensitive data| CSVGold[CSV Gold layer]

  JSON[JSON source data] --> |Data validation / ingestion fields| JSONBronze[JSON Bronze layer]
  JSONBronze --> |Standardising e.g. formats, units, naming conventions, data types etc.| JSONSilver[JSON Silver layer]
  JSONBronze --> |Failures on standardising data| JSONQuar[Quarantine]
  JSONSilver --> |Access controls, reports, filtering sensitive data| JSONGold[JSON Gold layer]

  Text[Text source data] --> |Data validation / ingestion fields| TextBronze[Text Bronze layer]
  TextBronze --> |Standardising e.g. formats, units, naming conventions, data types etc.| TextSilver[Text Silver layer]
  TextBronze --> |Failures on standardising data| TextQuar[Quarantine]
  TextSilver --> |Access controls, reports, filtering sensitive data| TextGold[Text Gold layer]

  Excel[Excel source data] --> |Data validation / ingestion fields| ExcelBronze[Excel Bronze layer]
  ExcelBronze --> |Standardising e.g. formats, units, naming conventions, data types etc.| ExcelSilver[Excel Silver layer]
  ExcelBronze --> |Failures on standardising data| ExcelQuar[Quarantine]
  ExcelSilver --> |Access controls, reports, filtering sensitive data| ExcelGold[Excel Gold layer]

  CSVGold --> Datamart[Datamart]
  JSONGold --> Datamart[Datamart]
  TextGold --> Datamart[Datamart]
  ExcelGold --> Datamart[Datamart] 

## Architecture
[TODO: Add architecture diagram]

See [docs/architecture/](docs/architecture/) for details.

## Setup

### Git

At a prompt copy and paste the following 2 lines:

```sh
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

### Local Development
```bash
# Clone this repository
git clone <repo url>
cd <repo_name>

# Confirm the Python 3 version
python --version

# Install dev dependencies (includes test tools, linting, docs)
pip install -r requirements_dev.txt

# Install the package in editable mode
pip install -e .

# Run tests
python -m pytest

# Run tests with a coverage report
python -m pytest --cov=src --cov-report=term-missing

# Run tests with an HTML coverage report
python -m pytest --cov=src --cov-report=html

# Run the pipeline
python -m data_processing.run_pipeline

# To push new code to GitHub
git status
git add .
git commit -m "New changes"
git push
```

## Project Structure
[TODO: Document your folder structure]

## Data Sources
[TODO: Describe the data files]

## Testing
[TODO: Document your testing approach]

Current coverage: [TODO: Add coverage badge]

## CI/CD
This project uses GitHub Actions for continuous integration.

See [.github/workflows/ci.yml](.github/workflows/ci.yml)

## Deployment to Fabric
[TODO: Document Fabric deployment process]

## Team
[TODO: Add team members]
