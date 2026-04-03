# University Course Registration System

## Team Members:
1. Clark, Emily [@Emc33728](https://github.com/Emc33728)
2. Park, Isabella [@jp09478](https://github.com/jp09478)
3. Patel, Siddh [@srp8](https://github.com/srp8)
4. Singh, Saachi [@Saachi715](https://github.com/Saachi715)

## Problem Description:
Our Course Registration Management System is designed to streamline the course enrollment process and enhance administrative efficiency in universities. This system facilitates key functions such as course scheduling, student enrollment, instructor assignments, and academic progress tracking. By centralizing data, our system minimizes scheduling conflicts, optimizes resource allocation, and ensures students have access to the courses they need. Additionally, it provides administrators with real-time insights into enrollment trends, faculty workload, and resource utilization, enabling data-driven decision-making. Ultimately, the Course Registration Management System supports the university’s mission of fostering academic success while improving operational efficiency and institutional growth.

## Data Model:

This data model showcases a university’s course registration system, including students, instructors, courses, enrollments, and grades. The Student entity is linked to the Enrollment entity, allowing for the tracking of student participation in various courses and maintaining academic records. The Instructor entity connects to the Course entity, ensuring that each course is assigned to a faculty member. Course details, such as course name, description, credits, and department, are stored within the Course entity, which helps manage academic offerings. Enrollment data is captured through the Enrollment entity, which records details like student ID, course CRN, and enrollment date, ensuring proper tracking of course registration. Lastly, the Grade entity connects to Enrollment, allowing for the recording of student performance, including letter grades, GPA equivalents, and grading dates. The relationships between these entities ensure comprehensive data storage for managing university operations, from course scheduling and faculty assignments to student progress tracking.  

The Student entity serves as the foundation of the data model. It stores key student information such as first name, last name, email, major, and enrollment date. The Student and Course entities share a many-to-many relationship, as each student can enroll in multiple courses, and each course can have multiple students. To properly represent this relationship, the Enrollment entity serves as the linking table, connecting students to the courses they register for. This joint table between Student and Course, forms a one-to-many relationship where a student can enroll in multiple courses, but each enrollment record belongs to only one student.  

The Instructor entity has a one-to-many relationship with the Course entity, as an instructor can teach multiple courses, but each course is assigned to only one instructor. The Enrollment entity also connects to the Course entity in a one-to-many relationship, ensuring that multiple students can enroll in a single course while maintaining an accurate record of enrollment history.  

When it comes to the Grade entity, it is connected to the Enrollment entity through a one-to-one relationship. Each enrollment record has a corresponding grade entry, tracking a student's performance in a specific course. The Grade entity ensures accurate academic tracking and helps in generating transcripts and GPA calculations.  

Finally, the relationships between these entities ensure a well-structured course registration system, allowing universities to efficiently manage student enrollments, faculty assignments, and academic progress while maintaining a streamlined and organized database.

<img width="584" alt="course_mgmgt_system" src="https://github.com/user-attachments/assets/049db44b-b73d-4d84-b0ee-03578bb6005d" />

## Data Dictionary:
<img width="480" alt="image" src="https://github.com/user-attachments/assets/49186adf-4f24-46f7-88fa-86569f228ef2" />

<img width="480" alt="image" src="https://github.com/user-attachments/assets/76abfd6b-b79d-4e10-aecb-629a921a7851" />

<img width="480" alt="image" src="https://github.com/user-attachments/assets/8bd16d84-f0b3-41e3-a106-c8a9aa7276d2" />

<img width="480" alt="image" src="https://github.com/user-attachments/assets/3e29699a-846d-44c3-ba05-8f6e8afb0f78" />

<img width="480" alt="image" src="https://github.com/user-attachments/assets/80f28669-153e-4a70-b8ad-e6f277975265" />

## Queries:
#### Query 1 - Identifying Courses with Low Averages
*Which courses have a class average of 75 or less and who is their course instructor?*

<img width="575" alt="image" src="https://github.com/user-attachments/assets/18d07dfe-13f6-4c60-9ad0-b420421e05a1" />
<img width="404" alt="image" src="https://github.com/user-attachments/assets/c9c168e6-4a1d-42e6-a360-0e70c6468765" />

This query helps identify courses where students may be struggling academically and can indicate issues such as challenging course material, ineffective teaching methods, or need for additional support. It provides two key insights: instructional effectiveness and curriculum challenges. For instance, if multiple courses taught by the same instructor have low averages, it may indicate a need for teaching adjustments or additional support. On the other hand, some courses may have outdated or overly difficult content, requiring curriculum updates or extra resources like tutoring. Identifying struggling courses early allows schools to take proactive steps and work toward improving student success and course quality.

#### Query 2 - Identifying Class Rosters
*How many students do instructors teach per class?*

<img width="836" alt="Screenshot 2025-03-12 at 8 52 55 PM" src="https://github.com/user-attachments/assets/305c2c26-0612-42c3-944f-a8d449991fa3" />
<img width="380" alt="Screenshot 2025-03-12 at 8 53 15 PM" src="https://github.com/user-attachments/assets/bc3dab16-6500-4e94-837f-bc1d11cc1d18" />

This query, in joining instructors to courses to enrollment, aids in finding the instructors with classes to large for one person's responsibility. By finding the number of students in each class, TA's can be properly and evenely assigned. Additionally, classes with large rosters could be split into smaller sections in future semesters so instructors are not over loaded. Offering more sections ensures students have better access to required courses, reduces scheduling conflicts, and improves the overall learning experience. 

#### Query 3 - Identifying Students' Courseloads
*How many courses is each student enrolled in?*

<img width="708" alt="image" src="https://github.com/user-attachments/assets/366a6fb2-cf27-42a3-86b6-9c266c5cb756" />
<img width="198" alt="image" src="https://github.com/user-attachments/assets/a250a81f-78a7-4a79-9079-a930f195dd03" />

By joining students to courses, this query lays out the students with the heaviest course loads. In answering the question of in how many courses is each student enrolled, the answer to typical class count is shown. This query also helps identify students that may be taking on too many classes and could be in need of assistance such as tutoring or stress relief. When it comes to scheduling finals at the end of the semester, this query is additionally useful for identifying potential conflicts for the students with the heaviest course loads. 

#### Query 4 - Indentifying Top-Performing Students
*Which student has the highest grade in each course?*

<img width="650" alt="image" src="https://github.com/user-attachments/assets/4459f242-1c21-4f2c-ae8e-0c7fe4764b34" />
<img width="300" alt="image" src="https://github.com/user-attachments/assets/494be9eb-7d33-41cd-a69b-fc7294c03a7f" />

This query identifies students with the highest grades in each course to track academic performance and recognize outstanding achievements by joining four tables—student, enrollment, grade, and course—to link student grades with their respective courses, with a subquery in the WHERE clause retrieving the maximum grade for each course to highlight top performers. This query supports the selection of teaching assistants (TAs) or scholarship candidates, facilitates academic performance monitoring and student recognition, and aids in identifying candidates for mentorship opportunities, providing a list of students with the highest grades per course.

#### Query 5 - Identifying Faculty Workload Distribution
*How many courses is each instructor responsible for?*

<img width="580" alt="image" src="https://github.com/user-attachments/assets/6b0a1d28-74bc-443c-97a9-cfc8ef6d6d3c" />
<img width="200" alt="image" src="https://github.com/user-attachments/assets/6ce1540c-9627-47af-9536-6df8daf05793" />

This query ensures balanced workloads and fair faculty assignments by counting the number of courses assigned to each instructor through a join of the course and instructor tables, with results grouped by instructor ID, and a subquery determining the maximum course count to highlight workload distribution. This query helps identify overburdened instructors who may need support, underutilized faculty who can take on more courses, and supports workload balancing to improve teaching quality and reduce burnout while also aiding in identifying faculty for promotion based on assignment data.

#### Query 6 - Identifying Students with Low GPAs
*Which students have a GPA of 2.00 or lower?*

<img width="653" alt="Screenshot 2025-03-12 at 6 24 47 PM" src="https://github.com/user-attachments/assets/ecfc7e1c-8b7c-4fee-8721-04add7473bbe" />
<img width="266" alt="Screenshot 2025-03-12 at 6 25 01 PM" src="https://github.com/user-attachments/assets/2838edeb-dd64-4caf-a429-c2a8e2cdecf5" />

This query recognizes students at risk of failing or potentially unable to graduate due to having low GPA. By identifying which students are struggling early, colleges can offer targeted support such as personal tutoring or academic counseling to help them stay on track and improve their performance. Which can help lead to higher graduation rates since students are able to receive the necessary resources to overcome academic challenges and succeed in their programs. Additionally by understanding any patterns in struggling students, universities can evaluate and adjust their policies and systems to ensure a more personalized approach to student success.


#### Query 7 - Identifying Students in the Database
*What are the details of all students enrolled ordered by their last name?*

<img width="477" alt="Screenshot 2025-03-12 at 6 47 19 PM" src="https://github.com/user-attachments/assets/3f75f22d-c8a4-46af-9bca-65befce73769" />
<img width="554" alt="Screenshot 2025-03-12 at 6 47 56 PM" src="https://github.com/user-attachments/assets/c9dbd80a-b924-4392-828d-1870342b7221" />

This query retrieves information about every enrolled student, including their student id, name, email, major, and enrollment date. Having the information ordered alphabetically by their last name creates an organized student directory which makes referencing, contacting, and managing student records easier. Additionally, it offers valuable insights for academic administration and student services, allowing them to effectively track and support their students.

#### Query 8 - Identifying Students that did not Receive Grades
*Which students have not received any grades?*

<img width="441" alt="image" src="https://github.com/user-attachments/assets/752ef426-e3dd-412d-9558-e6f9ea020144" />
<img width="289" alt="image" src="https://github.com/user-attachments/assets/91a55f0a-f7ff-4743-ba50-090f3efaec95" />

This query is highly useful for universities as it helps track students who are enrolled in courses but have not received any grades. By identifying these students, universities can proactively intervene to address potential issues such as course withdrawals, academic struggles, or administrative errors in grading. This is particularly valuable for academic advisors and faculty members who need to ensure that students are progressing toward their degrees. Additionally, by running a NOT EXISTS query, administrators can generate reports on students at risk of failing due to missing assessments or unrecorded grades. This insight enables universities to implement timely support measures, such as tutoring, counseling, or grade verification processes, ensuring academic success and retention.

#### Query 9 - Identify Students with Grade Variation
*Which students have the largest range among their grades?*

<img width="718" alt="Screenshot 2025-03-12 at 9 01 10 PM" src="https://github.com/user-attachments/assets/bc57bcd8-5667-42b7-8eeb-92ea89a0990a" />
<img width="268" alt="Screenshot 2025-03-12 at 9 05 02 PM" src="https://github.com/user-attachments/assets/f2b52807-021e-4f40-a740-461a539e227d" />

This query identifies students who have repeated a course and received different grade in it. It helps detect whether or not students who retake course are able to improve their grade. This information is useful for academic advisors and administrators to track student progress and identify if they need additional resources. It also allows universities to analyze trends in course performance and identify courses where students struggle, helping to allocate resources more effectively and improve overall academic success. Additionally, it could indicate a need for retake policies if students are retaking too many courses with minimal improvement. This ensures that students are not stuck in a cycle of retakes, promoting more effective academic progression and better use of university resources.

#### Query 10 - Identify Popularity of Major
*On average, what is the percent of total students per major?*

<img width="758" alt="Screenshot 2025-03-12 at 8 27 17 PM" src="https://github.com/user-attachments/assets/b4bf7828-54f3-4713-96d0-1832c2794a12" />
<img width="250" alt="Screenshot 2025-03-12 at 8 56 17 PM" src="https://github.com/user-attachments/assets/2c0df1e1-7817-45d6-bbf6-696ee8b332c5" />

This query employs built in functions and a subquery to identify the number of students and the percent of total students for each major. By identifying the most popular majors, courses and instructors can more proportionally be distributed. For instance, the MIS and Finance majors may need class sections added in future semesters to account for the larger classes because of the popularity of the major. While majors with lower enrollment can receive more support and resources to attract students to help to create a more balanced distribution across programs. Adtionally, the information from this query could also affect hiring decisions so that more instructors are staffed to handle the number of students in the larger majors.

## Database information:

<img width="741" alt="Screenshot 2025-03-12 at 9 18 07 PM" src="https://github.com/user-attachments/assets/47d2bc3b-d31a-4719-a831-476257fa9770" />

Name of the database: ha_group2_crn61608

All queries are bookmarked through stored procedures and can be called using this format: CALL TP_Qx(); where 'x' is the query number.
