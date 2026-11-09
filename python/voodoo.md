Voodoo Project Analyst:
------------------------------
- analyze this repository, create a markdown file called analysis.md with these categories:

0. Executive summary:
	- notes about each of the categories, maximum of 5 bullets
	- drop the stuff that is not interesting for C-level executives

1. Tech stack used (language, database, services)
	- analyze code and docker setup
	- analyze env file
	- check pipeline and workflows

2. Code quality:
	- pyright (or mypy) number of errors (strict mode) - separate subcategory; optionally also run astral ty as a fast second opinion (still beta, no stable API - expect false negatives vs pyright)
	- ruff number of coding style and linting issues - separate subcategory, create table, show amount of violations that can be automatically fixed by running fixer (e.g. ruff check --fix)
	- radon - all metrics (Cyclomatic Complexity, Maintainability Index, Raw metrics, Halstead metrics) - separate subcategory, create table
	- pylint - number of mess/code smell errors ruff doesn't cover (mainly refactor-level checks) - separate subcategory, create table
	- copy-paste detector (pylint similarities / jscpd) - summary of analysis 
	- structural observations - bullets, structured

3. Readme.md:
	- does it work - attempt project setup, check if docker images build, does the stack run
	- make sure its not deprecated and it's actually maintained and not generic framework readme
	- verify if all mentioned tools are indeed used in the project (npm, pip, poetry, uv, pipenv)

4. Database:
	- analysis of table structure
	- report of broken foreign keys, missing indexes on queried fields
	- if possible check for orphan entries
	- compare Python ORM models (SQLAlchemy/Alembic or Django ORM) schema with table state, find possible desync
	- do migrations pass when running from scratch
	- what tool is used for seeding/fixtures, does it correctly generate all the data (e.g. factory_boy, faker, fixtures)

5. Tests:
	- how many tests are written (number) and what framework is used for testing (i.e. pytest, unittest, playwright...)
	- run tests, show pass/failed metrics
	- if possible, calculate code coverage percentage (e.g. pytest-cov, coverage.py)
	- give recommendations on what critical parts to write tests for, if not written
	(i.e. financial calculations and authentication parts have prio over listing articles)
	- is there a test environment correctly setup (i.e. .env.test, .env.test.local, pytest.ini)

6. Security:
	- run bandit security scan (Python static AST code vulnerabilities)
	- run pip-audit vulnerability scan (Python dependency CVE scan)
	- run osv-scanner scan (free, no account; broader advisory coverage - replaces safety, which now requires account login)
	- run security cve vulnerability scan tool for npm (ask before installing) - npm audit or osv-scanner
	- run aikido security scan
	- check .env file for credentials
	- scan git history for leaked secrets (gitleaks / trufflehog)
	- scan built docker images for vulnerabilities (trivy)
	- check OWASP TOP 10 vulnerabilities

7. Libraries:
	- check for abandoned libraries
	- is the framework version in sunset or EOL, and how long (e.g. Django, FastAPI, Flask)
	- is the framework version getting security patches, and until when

8. Recommendations:
	- top 5 security risks (critical first)
	- top 5 things to improve in the codebase
	- recommendations of new tools and processes to introduce (i.e. pipelines, git hooks / pre-commit, linters)

Appendix:
- how the numbers were produced (where applicable)
