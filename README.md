# Flutter Lint Rules

This repository contains a custom `analysis_options.yaml` file for Flutter projects, designed to enforce consistent coding styles, best practices, and safety across development teams.

> ✅ Perfect for solo developers, teams, or open source projects.

---

## 📦 Features

- ✅ Enforces package imports (no relative imports in `lib/`)
- ✅ Encourages use of `final`, `const`, and trailing commas
- ✅ Helps keep your code clean, organized, and maintainable
- ✅ Prevents common pitfalls like `print()` in production code

---

## 📄 How to Use

1. **Copy the `analysis_options.yaml` file** into the root of your Flutter project.

2. In your project root:

   ```bash
   flutter pub get
   flutter analyze
   flutter fix --apply
   dart format .
