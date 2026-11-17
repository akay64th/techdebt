# Tech Debt Report: dotenv

## Metric definitions
- **Complexity**: Radon cyclomatic complexity per function (A=1-5, B=6-10, C=11-20, D=21-30, E=31-40, F=41+).
- **Function Length**: Physical lines of code from function definition to endline.
- **Size (SLOC)**: Source lines of code (excluding blanks and comments) per file.
- **Maintainability Index (MI)**: 0-100 composite score based on Halstead volume, CC, and SLOC (A: 20-100, B: 10-19, C: 0-9).
- **Import Coupling**: Count of distinct external/internal modules imported (higher = more coupled).
- **Duplication**: Repeated blocks of normalized consecutive lines across the codebase.
- **Hotspot score**: max-complexity rank + size rank per file (lower score = higher investigation priority).
- **Excluded paths**: test, tests, testing, docs, .github, .venv, venv, examples, locale.

## Complexity distribution
| Rank | Functions |
| --- | --- |
| A | 63 |
| B | 8 |
| C | 2 |
| D | 0 |
| E | 0 |
| F | 0 |

### Top 10 functions by complexity
| Function | File:Line | CC | Rank | Length (LOC) |
| --- | --- | --- | --- | --- |
| `set_key` | main.py:224 | 11 | C | 62 |
| `find_dotenv` | main.py:376 | 11 | C | 53 |
| `rewrite` | main.py:162 | 10 | B | 60 |
| `run` | cli.py:194 | 7 | B | 18 |
| `get_cli_string` | __init__.py:12 | 7 | B | 28 |
| `list_values` | cli.py:96 | 6 | B | 17 |
| `unset_key` | main.py:288 | 6 | B | 43 |
| `DotEnv._get_stream` | main.py:65 | 6 | B | 13 |
| `DotEnv.set_as_environment_variables` | main.py:101 | 6 | B | 14 |
| `parse_binding` | parser.py:144 | 6 | B | 41 |

### Five longest functions
| Function | File:Line | Length (LOC) | CC | Rank |
| --- | --- | --- | --- | --- |
| `DotEnv` | main.py:42 | 85 | 5 | A |
| `set_key` | main.py:224 | 62 | 11 | C |
| `rewrite` | main.py:162 | 60 | 10 | B |
| `find_dotenv` | main.py:376 | 53 | 11 | C |
| `run_command` | cli.py:214 | 51 | 4 | A |

## Hotspots (complex and large files)
| File | Max CC | SLOC | MI | Imports | Score |
| --- | --- | --- | --- | --- | --- |
| main.py | 11 | 353 | 40.89 (A) | 12 | 2 |
| cli.py | 7 | 182 | 56.58 (A) | 11 | 4 |
| parser.py | 6 | 149 | 45.77 (A) | 3 | 6 |
| variables.py | 4 | 64 | 44.29 (A) | 3 | 8 |
| __init__.py | 7 | 37 | 83.03 (A) | 3 | 8 |
| ipython.py | 3 | 41 | 100.0 (A) | 2 | 10 |
| __main__.py | 0 | 3 | 81.86 (A) | 1 | 13 |
| version.py | 0 | 1 | 100.0 (A) | 0 | 14 |

## Smells: self-admitted debt (1 found in 1 files)

### main.py (1 notes)
- Line 196 `[TEMPORARY]`: `# Report the target path, not the name of the temporary file.`

## Code Duplication (11 duplicate patterns detected)

#### Duplicate #1 (2 occurrences)
- cli.py:123-127
- cli.py:164-167

#### Duplicate #2 (2 occurrences)
- cli.py:124-128
- cli.py:165-168

#### Duplicate #3 (2 occurrences)
- cli.py:132-135
- cli.py:171-174

#### Duplicate #4 (2 occurrences)
- main.py:238-241
- main.py:301-304

#### Duplicate #5 (2 occurrences)
- main.py:239-242
- main.py:302-305

## What to investigate first
1. **Primary Hotspot**: Which file and function represent the highest immediate risk?
2. **Maintainability & Coupling**: Are the complex files also tightly coupled or poorly rated in MI?
3. **Smells & Duplication**: Do known debt comments align with the highest-risk hotspots?
