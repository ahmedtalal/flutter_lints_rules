# 📘 Flutter Lint Rules – Detailed Explanation

This document explains each lint rule in `analysis_options.yaml` and why it improves your Flutter/Dart project quality.

---

## 📦 Import Rules

[`always_use_package_imports`] : Forces you to use `package:my_app/xyz.dart` instead of relative imports. This improves clarity and prevents issues when refactoring or using shared modules.

[`avoid_relative_lib_imports`] : Prevents importing like `../lib/something.dart` which is messy and breaks modular structure.

[`depend_on_referenced_packages`] :Ensures all the packages you're importing are listed in `pubspec.yaml` so nothing "magically" works.

[`directives_ordering`] : Enforces proper order: `dart:` → `package:` → `your_project/` → `part`, which makes files cleaner and predictable.

[`unnecessary_import`] : Warns if you imported something but didn’t use it. Keeps your imports clean. |

---

## 🧱 Code Structure & Style

[`prefer_final_fields`] : Encourages using `final` for fields that are never reassigned. Makes your code more predictable and immutable by default.

[`prefer_final_locals`] : Same idea, but for **local variables** inside functions or methods.

[`prefer_const_constructors`] : If a widget or object is constant, use `const` to improve performance (const widgets are compiled at build time).

[`prefer_const_literals_to_create_immutables`] :Forces you to use `const` on collections (`List`, `Map`, `Set`) when possible, making them immutable.

[`sort_child_properties_last`] : In widgets, keeps `child:` at the bottom so it’s easier to find the UI component being nested. Improves readability.

[`require_trailing_commas`] :Encourages trailing commas in multi-line function calls or constructors, which improves `git diff` readability and formatting.

[`use_key_in_widget_constructors`] : Forces you to include `Key` in custom widget constructors to help Flutter track widgets correctly during rebuilds.

---

## 🔒 Safety & Clarity

[`always_specify_types`]: Enforces writing types like `String name = 'John';` instead of `var name = 'John';`. Improves readability and avoids unexpected behavior.

[`avoid_dynamic_calls`]: Disallows using `.something()` on variables of type `dynamic`. Encourages proper typing to prevent runtime errors.

[`unnecessary_this`] : Warns if you use `this.` where it’s not needed. Keeps code cleaner.

[`avoid_returning_null`] : Discourages returning `null` from functions. Helps avoid `null` errors. Prefer returning a default or using nullable types explicitly.

[`avoid_empty_else`] : If you write `if (...) {} else {}`, but the else block is empty, this warns you to remove it.

[`no_duplicate_case_values`] : Prevents accidental duplication of values in `switch` cases.

[`annotate_overrides`] : Forces the use of `@override` when overriding methods, improving clarity and tooling support.

---

## 🎯 Performance & Clean Code

[`avoid_unnecessary_containers`]: Warns when you use a `Container()` that does nothing. Helps avoid UI bloat.

[`sized_box_for_whitespace`] : Use `SizedBox` instead of `Container(width: 10)` when you only need spacing. More efficient and explicit.

[`unnecessary_lambdas`] : If you pass a function directly (e.g., `list.map(doSomething)`), there’s no need to wrap it in `() => doSomething()`.

[`prefer_single_quotes`] : Enforces using `'single quotes'` instead of `"double quotes"` (except when you need to use apostrophes in a string). Keeps consistency.

[`avoid_print`]: Prevents using `print()` in production. Prefer using a logging library like `logger` or `developer.log`.

---

## 🔗 IDE Integration

Use these settings to **auto-fix** most of these rules in VS Code:

```json
"[dart]": {
  "editor.codeActionsOnSave": {
    "source.organizeImports": true,
    "source.fixAll": true
  },
  "editor.formatOnSave": true
}
```

Or run manually:

```bash
flutter fix --apply
dart format .
```

---

## 📁 Suggested File Organization

- `analysis_options.yaml` → for the rules
- `README.md` → for general usage
- `RULES.md` → for detailed lint rule explanations (this file)
