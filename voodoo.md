Voodoo Project Analyst:
------------------------------
- analyze this repository, create a markdown file called analysis.md with these categories:

0. Executive summary:
	- notes about each of the categories, maximum of 5 bullets
	- drop the stuff that is not interesting for C-level executives

1. Tech stack used (langauge, databsae, services)
	- analyse code and docker setup
	- analyse env file
	- check pipeline and workflows

2. Code quality:
	- phpstan number of errors on level 9 - separate subscategory
	- phpcs number of coding style issues - separate subcategory, create table, show amount of violations that can be automatically fixed by running fixer
	- phpinsights - all four metrics - separate subcategory, create table
	- phpmd - number of mess errors - separate subcategory, create table
	- php copy paste detector - summary of analysis 
	- structural observations - bullets, structured

3. Readme.md:
	- does it work - attempt project setup, check if docker images build, does the stack run
	- make sure its not deprecated and it's actually maintained and not generic framework readme
	- verify if all mentioned tools are indeed used in the project (npm, composer)

4. Database:
	- analysis of table structure
	- report of broken foreign keys, missing indexes on queried fields
	- if possible check for orphan entries
	- compare php doctrine schema with table state, find possible desync
	- do migrations pass when running from scratch
	- what tool is used for seeding/fixtures, does it correctly generate all the data

5. Tests:
	- how many tests are written (number) and what framework is used for testing (i.e. phpunit, playwright...)
	- run tests, show pass/failed metrics
	- if possible, calculate code coverage percentage
	- give recommendations on what critical parts to write tests for, if not written
	(i.e. financial calculations and authentication parts have prio over listing articles)
	- is there a test environment correctly setup (i.e. .env.test.local)

6. Security:
	- run roave security scan (php projects)
	- run sensiolabs security scan (php projects)
	- run composer vulnerability scan (php projects)
	- run security cve vulnerability scan tool for npm (ask before installing) (javascript projects)
	- run aikido security scan
	- check .env file for credentials
	- check OWASP TOP 10 vulnerabilities

7. Libraries:
	- check for abandoned libraries
	- is the framework version in sunset or EOL, and how long
	- is the framework version getting security patches, and until when

8. Recommendations:
	- top 5 security risks (critical first)
	- top 5 things to improve in the codebase
	- recommendations of new tools and processes to introduce (i.e. pipelines, git hooks, linters)

Appendix:
- how the numbers were produced (where applicable)




