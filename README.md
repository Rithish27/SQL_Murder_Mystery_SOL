# SQL_Murder_Mystery_SOL
# solved using Basic SQL

This is an Intresting Murder Mystery one can solve using SQL (Structured Query Language) to find out "murdere" with basic SQL concepts.

-->There's been a Murder in SQL City! The SQL Murder Mystery is designed to be both a self-directed lesson to learn SQL concepts and commands and a fun game for experienced SQL users to solve an intriguing crime.

Crime Report: A crime has taken place and the detective needs your help. The detective gave you the crime scene report, but you somehow lost it. You vaguely remember that the crime was a ​murder​ that occurred sometime on ​Jan.15, 2018​ and that it took place in ​SQL City​. Start by retrieving the corresponding crime scene report from the police department’s database.

You can solve it here by your self:https://mystery.knightlab.com/


Here's the schema diagram
![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/19f3a66f-d87e-476b-8c43-2fcfc9a40f25)

Let's start

From the limited information we had we will start solving this case!
stage 1: We'll fetch the report from "crime_scene_report" table by the information we have
        SELECT *
        FROM crime_scene_report
        WHERE type = 'murder' AND 
              city = 'SQL City' AND 
              date=20180115;


![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/e888f655-7456-41cc-ba7c-3429b1778f57)

stage 2: From the above report we got to know that we got 2 witnesses.
         1—>last house on “Northwestern Dr’
         2—> name: ”Annabel” lives at "Franklin Ave"

         Let's find details about witnesses from "person" table.
         SELECT *
         FROM person
         WHERE address_street_name = "Northwestern Dr"
         ORDER BY address_number DESC
         LIMIT 1;

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/bf387121-aebe-41f7-9049-6667842792e7)

         SELECT *
         FROM person
         WHERE name like "Annabel%" AND address_street_name = "Franklin Ave" ;

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/8111b961-7e27-4f55-9b71-24854092e1a7)


stage 3: After finding details about witnesses let's see what they have to say about the murder!

         Explore the details about their interrogation from "interview" table
         

         



        


          
