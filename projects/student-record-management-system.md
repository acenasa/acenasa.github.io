---
layout: project
type: project
image: img/grades.jpg
title: "Student Record Management System"
date: 2024
published: true
labels:
  - C
  - Management System
summary: "A student record management system that I coded in C for ICS 212."
---

In ICS 212: Program Structure, a course I took in Spring 2024, I developed a student record management system using the C programming language. The goal was to create a terminal-based application that could **read**, **display**, **edit**, and **persistently save** student records stored in a binary file. This hands-on project helped me solidify my understanding of C structures, file I/O, modular functions, and robust user input validation.

The program interacts with a binary file named `students.data`, which stores records of student information in the form of a `Student` struct. Each record includes the student number, first and last names, age, and GPA. These structs are defined in an external header file, `student.h`, to keep the data model modular and clean.

## Core Functionality

The application begins by opening the binary file for reading and writing:

```c
filePointer = fopen(fileName, "rb+");
```

If the file cannot be opened, the program exits gracefully with an error message:

```c
if(filePointer == NULL){
    printf("File \"%s\" could not be opened. \n", fileName);
    exit(1);
}
```

### Reading and Displaying Records

Records are displayed using a loop with `fread()`:

```c
while (fread(&studentX, sizeof(Student), 1, filePointer)) {
    printStudent(studentX);
}
```

The `printStudent()` function formats and displays each record in a table, making it easy for users to visually browse the data:

```c
void printStudent(Student studentX){
    printf("%6d  %10s  %10s  %3d  %3.1f  \n",
           studentX.number,
           studentX.first,
           studentX.last,
           studentX.age,
           studentX.gpa);
}
```

### Editing a Specific Record

The user is prompted to choose a specific record to edit by entering its index. Input is validated using:

```c
int validateRecordNumber(int maxRecords);
```

This function ensures the record number is within bounds and discards any invalid input using a buffer-clearing loop:

```c
while (getchar() != '\n');
```

Once a valid record is selected, the program uses `fseek()` to navigate to the correct byte offset:

```c
fseek(filePointer, (recordNumber - 1) * sizeof(Student), SEEK_SET);
```

### Field Selection and Update

The user chooses which field to edit via the `getOption()` function. This validates the input to allow only 'f' (first name), 'l' (last name), 'a' (age), or 'g' (GPA):

```c
char getOption() {
    ...
    if (option != 'f' && option != 'l' && option != 'a' && option != 'g') {
        ...
    }
}
```

The `editRecord()` function then uses a `switch` statement to call `getstring()` for names, or `scanf()` for numerical fields:

```c
void editRecord(Student *studentX, int recordNumber, char option) {
    ...
    case 'g':
        printf("Enter GPA: ");
        scanf("%lf", &studentX->gpa);
        break;
}
```

### Persisting the Changes

After editing, the updated struct is written back to the file using `fwrite()`:

```c
fseek(filePointer, (recordNumber - 1) * sizeof(Student), SEEK_SET);
fwrite(&studentX, sizeof(Student), 1, filePointer);
```

### Closing the File

Proper cleanup ensures that the file is closed correctly, with user feedback depending on the return status:

```c
fileClosed = fclose(filePointer);
if(0 == fileClosed){
    printf("The file \"%s\" was successfully updated.\n", fileName);
}
```

## Reflection

This project taught me how to manage binary file data, handle user input safely, and build modular C programs using multiple source files and headers. I learned to think in terms of data offsets and memory layout, and I gained experience implementing validation loops, formatted output, and error handling.

To debug and experiment with logic, I also used AI tools like ChatGPT for quick prototyping and explanation of standard library functions, especially during asynchronous development. Completing this project gave me confidence in using C to build real-world, file-backed applications that simulate simple database functionality.

<hr>

Source: <a href="https://github.com/acenasa/student_record_management_system/blob/main/student_record_management_system.c"><i class="large github icon "></i>acenasa/ics-212-student-record-management-system</a>
