# Python Automated Testing with GitHub Actions

## Aim
Create a small Python project with unit tests and a GitHub Actions workflow that runs code checks and tests automatically on every push and pull request.

## Project structure

```text
python_ci_testing_project/
├── .github/
│   └── workflows/
│       └── python-tests.yml
├── tests/
│   └── test_calculator.py
├── calculator.py
├── requirements-dev.txt
├── .flake8
├── .gitignore
└── README.md
```

## Requirements
- Python 3.10 or newer
- Git
- A GitHub account (to see the hosted workflow result)

## Run locally

1. Open a terminal in this project folder.
2. (Optional) Create and activate a virtual environment.
3. Install the lint tool:

   ```bash
   python -m pip install -r requirements-dev.txt
   ```

4. Run linting:

   ```bash
   flake8 calculator.py tests
   ```

5. Run unit tests:

   ```bash
   python -m unittest discover -s tests -v
   ```

## GitHub Actions setup

1. Create a new empty repository on GitHub.
2. Extract this project ZIP and open a terminal inside the extracted folder.
3. Run these commands, replacing `YOUR-USERNAME` and `YOUR-REPOSITORY`:

   ```bash
   git init
   git add .
   git commit -m "Add Python tests and GitHub Actions workflow"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
   git push -u origin main
   ```

4. On GitHub, open the repository and select **Actions**.
5. Open **Python automated tests**. The workflow should run automatically after the push.
6. A green check means the lint and unit-test steps passed. A red cross means a step failed; open the run to read the logs.

## Expected workflow

The workflow runs on every `push` and `pull_request`:
1. Checks out the repository.
2. Sets up Python 3.12.
3. Installs Flake8.
4. Runs Flake8 lint checks.
5. Runs the unit tests using `unittest`.

## Example successful local result

```text
test_add (test_calculator.TestCalculator.test_add) ... ok
test_divide (test_calculator.TestCalculator.test_divide) ... ok
test_divide_by_zero_raises_error (test_calculator.TestCalculator.test_divide_by_zero_raises_error) ... ok
test_subtract (test_calculator.TestCalculator.test_subtract) ... ok

----------------------------------------------------------------------
Ran 4 tests in 0.001s

OK
```

The actual GitHub Actions result is generated only after you push the project to GitHub. This example is the expected local test output; it is not a claim that a GitHub-hosted run has already occurred.
