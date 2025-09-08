#!/usr/bin/env python3
"""
Environment Snapshot
- Collects basic OS and Python environment details
- Saves them into snapshot.json
"""

import os, platform, sys, json, datetime

def main():
    snapshot = {
        "timestamp": datetime.datetime.now().isoformat(timespec="seconds"),
        "os": platform.system(),
        "os_release": platform.release(),
        "os_version": platform.version(),
        "machine": platform.machine(),
        "processor": platform.processor(),
        "python_version": sys.version,
        "cwd": os.getcwd(),
        "env_vars_count": len(os.environ),
    }

    with open("snapshot.json", "w", encoding="utf-8") as f:
        json.dump(snapshot, f, indent=2)

    print("Environment snapshot saved to snapshot.json")

if __name__ == "__main__":
    main()
