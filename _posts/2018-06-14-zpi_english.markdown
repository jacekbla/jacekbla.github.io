---
layout: post_english
title:  "Team engineering project"
date:   2018-06-14 23:12:50 +0100
featured-img: zpi
categories: [eng]
---
Project implemented in a group of four. As part of the Team Engineering Project course, our task was to design and implement a web application for forming and working with groups implementing other projects in the field of these classes.
The application has been divided into two parts, frontend, mainly using the *Angular* framework and backend, written in *Java*, based on the *Spring Boot* tool. The program stored data in a remote **MySQL** database. My task was to prepare the database design, implementation, implementation and communication with the backend.

![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/zpi/scheme.jpg)

From the user's side, the application consisted of two parts:
- Student website
    - Allows you to search for existing groups that are looking for team members.
    - Allows you to go to the tab illustrating the current student group. Group information (members, subject, technologies), other members' submissions and the option to leave the group are displayed.
    - Includes a personal profile tab showing a list of your own submissions to other groups. It also contains various information about the student, in addition it is possible to go to the view, which shows a list of preferred technologies that we can change - they affect the groups proposed to the user.


    ![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/zpi/student.jpg)

- Host site
    - Contains a list of all groups in the database along with information about the topic, leaders, members and technologies.
    - Displays all groups of the lecturer along with information about them and allows their modification. An option to add a new group is also available.
    - Includes a personal profile tab where the teacher can find and modify his own information and has a preview of all students whose projects he leads.


    ![](https://raw.githubusercontent.com/jacekbla/jacekbla.github.io/master/assets/img/posts/content/zpi/leader.jpg)