# Automated Log Analyzer

A dependency-free command-line tool that scans log files and directories, counts common log levels, and reports recurring messages.

## Run

From the project directory:

```powershell
python -m log_analyzer path\to\app.log
python -m log_analyzer path\to\logs --format json
```

Directories are scanned recursively. Multiple files and directories can be supplied in one command. Text is read as UTF-8, replacing invalid byte sequences so one malformed character does not stop a scan.

To install the `log-analyzer` command in the active Python environment:

```powershell
python -m pip install -e .
log-analyzer path\to\app.log
```

Recognized levels are DEBUG, INFO, NOTICE, WARN/WARNING, ERROR/ERR, and CRITICAL/FATAL. NOTICE is counted as INFO, WARN as WARNING, ERR as ERROR, and FATAL as CRITICAL. Blank lines are ignored; nonblank lines without a recognized level are counted as unmatched. Repeated messages are normalized for timestamps and whitespace.

## Tests

```powershell
python -m unittest discover -s tests -v
```
