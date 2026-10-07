# Linux File System Navigation & Access Auditing

## Project Overview
This repository contains documentation from a practical lab completed as part of the **Google Cybersecurity Certificate**. The objective was to navigate a remote Linux file structure via the Bash shell to locate, examine, and extract critical information from user access reports and server logs.

As a security analyst, navigating servers without a Graphical User Interface (GUI) is an essential skill. Efficient command-line navigation enables rapid incident response, precise log file analysis, and reliable access control auditing.

## Key Skills & Tools Demonstrated
* **Environment:** Qwiklabs Virtual Machine (Linux Bash Shell)
* **CLI Navigation:** `pwd` (Print Working Directory), `cd` (Change Directory), `ls` (List)
* **File Reading & Parsing:** `cat` (Concatenate)
* **Core Competencies:** Environment reconnaissance, log file analysis, access control auditing, and remote server navigation.

---

## Lab Execution & Operational Walkthrough

### 1. Environment Reconnaissance
The first objective during any remote investigation is establishing the current working directory to orient the session. 
```bash
analyst@524cb0bc3715:~$ pwd
/home/analyst
```

### 2. Navigating to Compliance Reports
The investigation required navigating into the reports directory to locate specific subdirectories containing user data. I verified the path change and listed the contents to find the `users` directory.
```bash
analyst@524cb0bc3715:~$ cd reports
analyst@524cb0bc3715:~/reports$ pwd
/home/analyst/reports
analyst@524cb0bc3715:~/reports$ ls
users
```

### 3. Auditing User Access Controls
To verify recently added users for compliance auditing, I navigated to the `users` subdirectory and read the contents of the newly generated text file[cite: 6]. This allowed me to extract specific employee identifiers and department assignments (e.g., verifying user `mreed` in Information Technology and `aezra` in Human Resources)[cite: 6].
```bash
analyst@524cb0bc3715:~/reports$ cd users
analyst@524cb0bc3715:~/reports/users$ ls
Q1_added_users.txt  Q1_deleted_users.txt
analyst@524cb0bc3715:~/reports/users$ cat Q1_added_users.txt
employee_id  username  department
1001         bmoreno   Marketing
1026         apatel    Human Resources
1041         cgriffin  Sales
1104         mreed     Information Technology
1177         aezra     Human Resources
1188         noshiro   Finance
```

### 4. Comprehensive Server Log Analysis
Finally, I returned to the home directory and navigated into the server logs directory[cite: 6]. To investigate recent system events, I utilized the `cat` command to output the entirety of `server_logs.txt`, revealing a sequence of unauthorized access attempts, incorrect passwords, and storage capacity warnings[cite: 6].
```bash
analyst@524cb0bc3715:~/reports/users$ cd
analyst@524cb0bc3715:~$ cd logs
analyst@524cb0bc3715:~/logs$ ls
server_logs.txt
analyst@524cb0bc3715:~/logs$ cat server_logs.txt
2022-09-28 13:55:55 info    User logged on successfully
2022-09-28 13:56:22 error   The password is incorrect
2022-09-28 13:56:48 warning The file storage is 75% full
2022-09-28 15:55:55 info    User logged on successfully
2022-09-28 15:56:22 error   The username is incorrect
2022-09-28 15:56:48 warning The file storage is 90% full
2022-09-28 16:55:55 info    User navigated to settings page
2022-09-28 16:56:22 error   The password is incorrect
2022-09-28 16:56:48 warning The current user's password expires in 15 days
2022-09-29 13:55:55 info    User logged on successfully
2022-09-29 13:56:22 error   An unexpected error occurred
2022-09-29 13:56:48 warning The file storage is 90% full
2022-09-29 15:55:55 info    User navigated to settings page
2022-09-29 15:56:22 error   Unauthorized access
2022-09-29 15:56:48 warning The file storage is 75% full
2022-09-29 16:55:55 info    User requested security reports
2022-09-29 16:56:22 error   Unauthorized access
2022-09-29 16:56:48 warning The current user's password expires in 15 days
```

---

## Result & Business Impact
* **Compliance Verification:** Efficiently navigated directory trees to locate and audit employee access files natively from the command line.
* **Incident Triage:** Successfully extracted and reviewed raw server logs to identify potential security incidents, including recurring unauthorized access attempts and storage threshold warnings.
* **CLI Proficiency:** Proved capability to operate and investigate within remote, GUI-less environments, a mandatory skill for cloud security and infrastructure management.
