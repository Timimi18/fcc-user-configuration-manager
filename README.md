# User Configuration Manager (freeCodeCamp Project)

A Python application that serves as a lightweight configuration management system. It allows users to dynamically manage system settings (such as UI themes, localization languages, and toggle notifications) using robust CRUD (Create, Read, Update, Delete) operations.

This project was built to satisfy 100% of the user stories and test suites for the **freeCodeCamp Python Certification** curriculum.

## 🚀 Project Objectives & User Stories
The manager strictly implements the following programmatic rules:
1. **add_setting(settings, (key, value)):** Validates input, converts values to lowercase, protects existing records from being overwritten, and appends new preferences.
2. **update_setting(settings, (key, value)):** Safeguards against altering non-existent configurations while handling updates gracefully.
3. **delete_setting(settings, key):** Safely purges configuration settings from memory with built-in missing key errors.
4. **view_settings(settings):** Formats active parameters into a clean, human-readable console string with auto-capitalized headers.

## 🛠️ Core Technical Concepts Demonstrated
* **Data Structures:** Leveraging Python `dictionaries` for O(1) constant-time configuration lookups and `tuples` for immutable data parsing.
* **String Manipulation:** Advanced usage of string formatting (f-strings) combined with text case management methods (`.lower()` and `.capitalize()`).
* **Defensive Programming:** Implementation of edge-case verification blocks to handle empty dictionaries, non-matching keys, and duplicate record collisions.

## 📂 Source Code Snapshot
```python
# The complete core logic developed to pass the freeCodeCamp test specifications:

def add_setting(settings, key_value):
    key = key_value[0].lower()
    value = key_value[1].lower()
    if key in settings:
        return f"Setting '{key}' already exists! Cannot add a new setting with this name."
    settings[key] = value
    return f"Setting '{key}' added with value '{value}' successfully!"

def update_setting(settings, key_value):
    key = key_value[0].lower()
    value = key_value[1].lower()
    if key not in settings:
        return f"Setting '{key}' does not exist! Cannot update a non-existing setting."
    settings[key] = value
    return f"Setting '{key}' updated to '{value}' successfully!"

def delete_setting(settings, key):
    key = key.lower()
    if key not in settings:
        return "Setting not found!"
    del settings[key]
    return f"Setting '{key}' deleted successfully!"

def view_settings(settings):
    if not settings:
        return "No settings available."
    output = "Current User Settings:\n"
    for key, value in settings.items():
        output += f"{key.capitalize()}: {value}\n"
    return output
```
