## Exercice 5 (Repo 1): "Java Report for BankApplication" (GitHub Actions - Simple Workflow)

```
name: Java File Report

on:
  push:
  pull_request:

jobs:
  java-report:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Scan Java files and generate report
        run: |
          set -e

          # Find Java source files
          JAVA_FILES=$(find . -type f -name "*.java")

          # Fail if no .java files
          if [ -z "$JAVA_FILES" ]; then
            echo "No .java files found"
            exit 1
          fi

          # Fail if any .class files exist
          CLASS_FILES=$(find . -type f -name "*.class")
          if [ -n "$CLASS_FILES" ]; then
            echo "Compiled .class files found (bad practice):"
            echo "$CLASS_FILES"
            exit 1
          fi

          # Generate report
          REPORT="java-file-report.txt"
          echo "Java File Report" > $REPORT
          echo "================" >> $REPORT
          echo "" >> $REPORT

          FILE_COUNT=0
          TOTAL_LINES=0

          echo "Per-file breakdown:" >> $REPORT

          for file in $JAVA_FILES; do
            LINES=$(wc -l < "$file")
            echo "$file – $LINES" >> $REPORT
            FILE_COUNT=$((FILE_COUNT + 1))
            TOTAL_LINES=$((TOTAL_LINES + LINES))
          done

          echo "" >> $REPORT
          echo "Summary:" >> $REPORT
          echo "Number of .java files: $FILE_COUNT" >> $REPORT
          echo "Total lines of code: $TOTAL_LINES" >> $REPORT

      - name: Upload report artifact
        uses: actions/upload-artifact@v4
        with:
          name: java-file-report
          path: java-file-report.txt

```

Voici le fichier `main.yml`, il permet de vérifier que l'on peut scanner les documents `.java` et ensuite ressortir : le chemin vers le fichier, le nombre de ligne de chaque fichier, ainsi que des données globales tel que le nombre de fichiers `.java` et le nombre total de ligne de code.

```
Java File Report
================

Per-file breakdown:
./src/test/java/bankAccountApp/PersonTest.java – 228
./src/test/java/bankAccountApp/AllTests.java – 11
./src/test/java/bankAccountApp/BankAccountTest.java – 205
./src/test/java/bankAccountApp/BankTest.java – 148
./src/test/java/bankAccountApp/ACHServiceTest.java – 58
./src/main/java/bankAccountApp/ACHService.java – 25
./src/main/java/bankAccountApp/BankAccountApp.java – 220
./src/main/java/bankAccountApp/Bank.java – 203
./src/main/java/bankAccountApp/Person.java – 273
./src/main/java/bankAccountApp/ACHServiceImpl.java – 19
./src/main/java/bankAccountApp/BankAccount.java – 221

Summary:
Number of .java files: 11
Total lines of code: 1611
```
