<h1>File Permissions in Linux</h1>
<h2>Description</h2><br>
The following activity displays my examples of using Linux, such as:<br>
<li>Screenshots of commands or typed versions of the commands</li>
<li>Explanations of commands</li>
<li>A project description at the beginning</li>
<li>A summary at the end</li>
<li>Details on using <b>chmod</b> to update file permissions</li>
<li>Details on checking file permissions with <b>ls -la</b></li>
<li>Details on interpreting the 10-character string that represents file permissions</li>
<li>Details on hidden files and directories</li>
<br>
<h2>Scenario</h2>
Our security team was tasked to update file permissions for specific files and directories in our projects directory. There are a few authorizations that need to be modified within the user, group, and 'other' categories. My job is to ensure that the users on the team are authorized with the appropriate permissions. Below will demonstrate the Linux commands that I used to do the following tasks: check permissions and modify any reading, writing, and/or executive access for the user, group, or 'other'.<br>

<h2>Check file and directory details</h2>
The following demonstrates how I used Linux commands to determine the existing permissions for a specific directory (projects) in the file system:<br><br>

![Model](https://private-user-images.githubusercontent.com/150729908/296940521-6e634e28-2c47-4b10-beb0-8a4b2b835667.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDUzODMwNzcsIm5iZiI6MTcwNTM4Mjc3NywicGF0aCI6Ii8xNTA3Mjk5MDgvMjk2OTQwNTIxLTZlNjM0ZTI4LTJjNDctNGIxMC1iZWIwLThhNGIyYjgzNTY2Ny5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExNlQwNTI2MTdaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kYWRmYjQ4NzRhNzc2Mjk5YzZiMWZhMzQxOWQ4OWFkZDIwMmUyM2U3MGRlMWRjNjgwYzFmMWJiZTk3MmQyNWVhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9._RgJNlfw4ZOoz1RnQQ5uBmr_H_-doaANw5necFvKZPo)<br><br>
The first command I used (first line), ls, shows the subdirectories that are listed under projects, including a hidden one, drafts. The next command I used to check permissions for the projects directory was ls -la (3rd line). This displayed the outputs in the file. This displayed all the file contents, including 3 hidden files: the first two files above .project_x.txt, and also below it that's named drafts.<br><br>

<h2>Describe the permissions string</h2>
Using the screenshot displayed above (in the "Check file and directory details" section) the 10-character string is the first column to the left of the screenshot, that shows 10 characters, each of them representing permissions for either the user, group, or 'other'. The D represents directory (which is the 1st character), the R stands for reading, the W stands for writing, and the X stands for execution. The 2nd-4th characters apply to the user. The 5th-7th characters apply to the group of users. The 8th-10th characters apply to 'other'.<br><br>

As an example (from the screenshot above) I will use project_k.txt. In project_k.txt, the 10-character string displays -rw-rw-rw-. What this shows is that all three owners (user, group, and other) have r and w. The r means read and the w stands for write. The hyphen sign as the first character means that it's a regular file and not a directory. The remaining hyphens mean that there are no other permissions for each of the user, group, or other (so the first rw- means that the user has access to read and write, but does not have execution access). Therefore, all three owners have permission to read and write in the project_k.txt file.<br><br>

<h2>Change file permissions</h2>
Our team was informed that 'other' should not have writing permission to any of their files. Therefore, the file that needed to be modified was project_k.txt. The command I used was chmod o-w project_k.txt (first line in the screenshot below). I then used the 'ls -la' command to bring up the updated files, and it confirmed that the writing access for 'other was deleted for that specific file (8th line, it was originally -rw-rw-rw-, now it's -rw-rw-r--):<br><br>

![Model](https://private-user-images.githubusercontent.com/150729908/296942469-03198cde-9763-4df2-8af5-d8da1569fb8d.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDUzODM3OTksIm5iZiI6MTcwNTM4MzQ5OSwicGF0aCI6Ii8xNTA3Mjk5MDgvMjk2OTQyNDY5LTAzMTk4Y2RlLTk3NjMtNGRmMi04YWY1LWQ4ZGExNTY5ZmI4ZC5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExNlQwNTM4MTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hNmI0ZTI2M2QxMTkwYzA3ZDUyZmE4MTBlZWUyOTNiYTIzYjhiNGE2MDI0ZjNlMjc2ZTZlZjkyMzU1YzQ4OWMxJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.lrlJSNIXBCxGk6oBbuVLlO0cs3RAIin31H8pvXZ6YY0)<br><br>

<h2>Change file permissions on a hidden file</h2>
It was noted that the company didn't want anyone in the .project_x.txt file to have write access to this project. Unfortunately, both the user and group still have writing access. They also wanted the group to at least have reading access. The command I used to modify .project_x.txt was the following:<br><br>

chmod u-w,g-w,g+r .project_x.txt<br><br>

I then used 'ls -la' to open up the updated files to see the changes that were made. The chmod command took away writing access for both user and group, while also adding reading access to group, so that both user and group have reading access to the file (screenshot below, 6th line):<br><br>

![Model](https://private-user-images.githubusercontent.com/150729908/296944183-e2cca430-0f77-4875-b9e8-8ff7adb0d7e6.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDUzODQzOTIsIm5iZiI6MTcwNTM4NDA5MiwicGF0aCI6Ii8xNTA3Mjk5MDgvMjk2OTQ0MTgzLWUyY2NhNDMwLTBmNzctNDg3NS1iOWU4LThmZjdhZGIwZDdlNi5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExNlQwNTQ4MTJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yODY1NjNmMjc2NmRjYTQ1N2FjMWVmZDY0ZWZjMDRmZjJmOTk2MDE2YmQ3YTI0Njg2YzE0NjFhZjQ0MjM2NThlJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.Oww992xwqk4zL-C3g13mSTT_6P5jxDymCMYHQmdOPTo)<br><br>

<h2>Change directory permissions</h2>
The next task was for the researcher2 user to be the only one to have access to the drafts file and its contents. The command I used was the following:<br><br>

chmod g-x drafts<br>
(first line in the screenshot below)<br><br>

This took away executive (x) access for group (7th line in the screenshot), allowing only researcher2 (user) to have full access to the drafts. The command 'ls -la' was used (2nd line) to see the updated modfications:<br><br>

![Model](https://private-user-images.githubusercontent.com/150729908/296946513-292c2c45-b099-4b6f-ab72-032bcb381516.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDUzODUxMzksIm5iZiI6MTcwNTM4NDgzOSwicGF0aCI6Ii8xNTA3Mjk5MDgvMjk2OTQ2NTEzLTI5MmMyYzQ1LWIwOTktNGI2Zi1hYjcyLTAzMmJjYjM4MTUxNi5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwMTE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDExNlQwNjAwMzlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00OGQ5NDBlN2EzNTU5ZmY3MDBjMjc5NDhlZDU0ZDYxNGU5NGQ0ZTYzODFjNDg4ZjQ2MWViMmY5NDNjMWRkMzYwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.UHMYi3Fzf21GysTGS4DYM99cz4ZQDAgffy2kliHabfc)<br><br>

<h2>Summary</h2>
In the scenarios above, I demonstrated the Linux commands that were used to modify permissions for the various users under the project directory. The command ls -la was used to display the current permissions for each file in the directory. Some permissions needed to be modified, and that was displayed using chmod command. After each modification, I followed up by using ls -la to display all the permissions to the files and directories again to display the updated modifications to the files.<br>


<!--
 ```
 This File Permissions in Linux Repository contains the following:
 File Permissions in Linux

 The scenario listed above is taken from one of the Activities sections provided by the Google Career Cybersecurity Certificate.
```
--!>