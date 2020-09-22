# Moodle Database: Educational Data Log Analysis 
## Overview
This week you will analyse the 2019 10 Academy learners activity in the Moodle Learning Management System. The moodle LMS is a highly scalable framework, and all students activities are stored in a highly structured database.  

## Business Need
Many educational facilities such as colleges, universities, bootcamps rely on scalable and versatile Learning Management Systems. 

The Moodle LMS  is a free and open-source learning management system written in PHP and distributed under the [GNU General Public License](https://en.wikipedia.org/wiki/Moodle). It is used for blended learning, distance education, flipped classroom and other e-learning projects in schools, universities, workplaces and other sectors. With customizable management features, it is used to create private websites with online courses for educators and trainers to achieve learning goals. Moodle allows for extending and tailoring learning environments using community-sourced plugins.

In 2019, 10 Academy used the Moodle LMS to manage about 1000 students in their 6 months data science training. Learners, course instructors, and all admins interacted with the Moodle system for almost all the training activities. All events from these activities are logged in the moodle postgres database. 

10 Academy, like any other educational facility, is interested to understand the learners skill and knowledge development, and is interested to build models that are able to predict possible dropouts as well as classify learners into doing, well, doing ok, and struggling groups. 10 Academy is also interested in automating the process of reminding learners approaching deadlines, providing quick feedback based on their overall community engagement and performance. Moreover, given the main goal of 10 Academy training is to make students job ready, it wants to measure students' performance across many relevant metrics. 

**Challenge**:
assuming a role-model of a freelancer hired by 10 Academy, you are to explore the 10 Academy Moodle logs stored in the database together with many other relevant tables. By the end of your analysis, you are expected to build a Tableau dashboard that illustrates the progress of students across time.
## Data: 
You can download the anonymised 10 Academy moodle postgres database copy [here](https://drive.google.com/file/d/1JQT4wDgH1qJQ_ghrn9tt6nU3XckihlUc/view?usp=sharing).

Check this [reference](https://kb.objectrocket.com/postgresql/use-postgresql-to-backup-and-restore-data-1159) for commands used to restore a postgres database from pg_dump generated .sql file - which is what you download with the link given above. In general it is a three step process 
1. Download and install postgres database if it is not already installed in your computer
2. In the command line create a database named *moodle* with psql for the user *your_user_name* $ sudo -u {your_user_name} createdb moodle


3. Add the tables from the dump to the local database you just created $ psql -U tenac -d moodle  -f devmoodle_anonymised.sql

## Moodle logs
The first place to start to understand moodle logs is to understand the model of events in moodle [here](https://docs.moodle.org/dev/Event_2). In the link, the description of the log column names are also explained.
For dashboard creation illustrating users engagement can be extracted using moodle log. For more information on how to do analytics with moodle log entries, see this . Important columns to know:

*Events*: 
Events are atomic pieces of information describing something that happened in Moodle. Events are primarily the result of user actions, but could also be the result of the [cron](http://docs.moodle.org/en/Cron) process or administration actions [undertaken via the command line](http://docs.moodle.org/en/Administration_via_command_line). 

## Most Important Tables (MIT)

Moodle database is complex - with more than 400 connected tables! In this project we are interested only in the subset of the tables. The most important tables we will consider in this challenge are (tables in bold are VIP)

- mdl_logstore_standard_log
- mdl_context
- mdl_user
- mdl_course
- mdl_modules 
- mdl_course_modules
- mdl_course_modules_completion 
- mdl_grade_items
- mdl_grade_grades
- mdl_grade_categories
- mdl_grade_items_history
- mdl_grade_grades_history
- mdl_grade_categories_history
- mdl_forum
- mdl_forum_discussions
- mdl_forum_posts

## Learning Outcomes
- Understanding complex database schema
- Understanding how user interactions data is modeled using events
- Working with postgres database  
- Educational logs data exploration 
- Education data mining
- Complex Tableau dashboard building 
