---
layout: page
title: GitHub Classroom
parent: Course Procedures
nav_order: 3
---

# How to Use GitHub Classroom

## Introduction

GitHub Classroom is a platform that helps students manage and submit coding assignments using GitHub repositories. This guide explains the steps to get started and successfully complete assignments.

## Getting Started

1.  **Accepting an Assignment**
    *   Your instructor will provide a link to a GitHub Classroom assignment.
    *   Click the link and sign in with your GitHub account.
    *   Authorize GitHub Classroom if prompted.
2.  **Repository Creation**
    *   After accepting, a new private repository is created for you.
    *   The repository is named according to the assignment and your username.

## Working on Your Assignment

If you prefer to work from the command line, follow these steps:

1.  **Cloning the Repository**
    *   Copy the repository URL from GitHub.
    *   Open your terminal and run:
        ```
        git clone <repository-url>
        ```
    *   This downloads the assignment files to your computer.
2.  **Editing Files**
    *   Open the files in your preferred code editor.
    *   Complete the tasks as described in the assignment instructions.
3.  **Committing Changes**
    *   After making changes, save your files.
    *   In the terminal, run:
        ```
        git add .
        git commit -m "Completed assignment"
        git push
        ```
    *   This uploads your work to GitHub.

## Alternative: Downloading and Uploading Files Manually

If you are not comfortable using Git or the command line, you can work with your assignment by downloading and uploading files through the GitHub website:

1.  **Downloading the Repository**
    *   Go to your assignment repository on GitHub.
    *   Click the green `Code` button and select `Download ZIP`.
    *   Extract the ZIP file to your computer.
2.  **Editing Files**
    *   Open the extracted files in your code editor.
    *   Complete the assignment as instructed.
3.  **Uploading Your Work**
    *   After finishing, return to your repository on GitHub.
    *   Click `Add file` -> `Upload files`.
    *   Drag and drop your updated files, then click `Commit changes`.

**Warning:** This manual method is not recommended for regular use. It can lead to mistakes, lost work, or overwritten files, especially for larger projects. Learning to use Git and the command line will help you work more efficiently, keep track of changes, and collaborate with others. Consider investing time to learn Git---it is a valuable skill for any programmer or engineer.

## Submitting Your Assignment

Pushing your changes to GitHub usually counts as submitting your assignment. Check the assignment instructions for any additional submission steps.

## Tips

*   Commit and push your work regularly to avoid losing progress.
*   Use GitHub Issues or Discussions if enabled to ask questions.
*   Review feedback from your instructor in the repository.
*   It is worth your time to set up SSH keys if you are using the same computer routinely.

## Troubleshooting

*   If you have trouble cloning or pushing, check your internet connection and GitHub authentication.
*   Contact your instructor if you encounter repository access issues.
