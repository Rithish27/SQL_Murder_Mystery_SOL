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
        Fetch report from "crime_scene_report" table
        
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
        
        SELECT *
        FROM interview
        WHERE person_id = 14887;

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/29090e9f-5f97-45dd-a8b6-2df0fa7510a1)

        SELECT *
        FROM interview
        WHERE person_id = 16371;

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/88908af7-21e2-41cd-924a-6240c863a4f9)

stage 4: From the interrogation we can search for the murderer with the details we have
        Search for suspect from "get_fit_now_member" table
        
        SELECT *
        FROM get_fit_now_member
        WHERE membership_status = 'gold' AND id LIKE "48Z%";


![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/3d345309-0b39-4be9-a947-4103eddb0dc4)

stage 5: We got the details of two suspects by this information.
        Let's explore the interview table and search for interrogation.
        
        SELECT *
        FROM interview
        WHERE person_id in (28819,67318);

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/7c46f658-b4fb-4be3-a8bb-e7c3529c5e1f)

stage 6: We found the one who did it but need to find the master mind behind this!

        From the limited data that we have we can search for "Master Mind Behind"

        We can search for people who attended event from "facebook_event_checkin" table

        SELECT COUNT(person_id) as no_of_times,person_id
        FROM facebook_event_checkin
        WHERE event_name = "SQL Symphony Concert" AND (date > 20171201 AND date < 20171231)
        GROUP BY person_id
        ORDER BY COUNT(person_id) DESC;

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/c57c6d92-cfaf-47d9-86f5-c33acf9ac345)

stage 7: We found that there are two suspects from the info that we have.
        Let's get more details about suspects from "person" table
        
        SELECT *
        FROM person
        WHERE id in (24556,99716);
        
![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/dc7a4487-c5a1-4be6-a06f-434621ce3d81)

        --> we also know that she had a lot of money in her account (ssn number)
        Let's find who had more money in account to pay "HIT MAN"
        
        SELECT *
        FROM income
        WHERE ssn in (816663882,987756388);

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/ff392709-3186-4b43-a22b-5190d890de3f)

        --> By simply finding the person with this ssn number we can find who's is the actual "Murderrer"


SOL:--> "Miranda Priestly" is the actual Murderrer

Let's check for our solution

![image](https://github.com/Rithish27/SQL_Murder_Mystery_SOL/assets/91436355/d978dd96-e2ce-4fd8-a7bb-79c9e436881e)


Thank you for reading!


credits:
The SQL Murder Mystery was created by Joon Park and Cathy He while they were Knight Lab fellows. See the GitHub repository "https://github.com/NUKnightLab/sql-mysteries" for more information.Adapted and produced for the web by Joe Germuska.








         

         



        


          
