---
layout: project
type: project
image: img/grades.jpg
title: "Ashwagandha Research Paper"
date: 2024
published: true
labels:
  - C
  - Management System
summary: "A student record management system that I coded in ICS 212."
---

In ICS 212 Program Structure, a class I took in Spring 2024, we were tasked with creating a student record management system that could read, display, edit, and save student data in a binary file format. The program begins by opening an existing file, `students.data`, which contains records of students, each including fields such as student number, first and last names, age, and GPA. It reads and displays all records for the user in a tabular format, providing a clear view of the data. The program then allows the user to select a specific record by its number and edit fields such as first name, last name, age, or GPA. Once the edits are made, the updated record is written back to the file. This ensures that all changes are saved persistently, allowing the system to function as a simple database for managing student records.

The program incorporates robust user input validation to ensure that record numbers are within range and that field edits are properly formatted, minimizing the chance of errors. For example, the `validateRecordNumber` function ensures that the selected record exists, while the `getOption` function guides the user to choose valid fields for editing. I used modular design principles by implementing helper functions like `printStudent`, `editRecord`, and others to keep the code organized and maintainable. This project was completed online asynchronously under Professor William "Bill" Wright at Leeward Community College. To troubleshoot and improve efficiency, I occasionally used ChatGPT for debugging and code validation, ensuring that I fully understood the logic behind each function. The program performed flawlessly, reinforcing my knowledge of file I/O, structures, and user interaction in C, while also providing valuable insights into creating functional, real-world applications.

<hr>

Source: (to be added)
